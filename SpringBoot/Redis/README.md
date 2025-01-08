使用FastJson2解决Redis序列化问题

```java

/**
 * 解决Redis序列化问题
 */
@Configuration
public class RedisConfig {
    @Bean("redisTemplate")
    public RedisTemplate<String,Object> redisTemplate(RedisConnectionFactory factory){
        //我们为了开发方便，一般直接使用<String, Object>
        RedisTemplate<String, Object> template = new RedisTemplate<String,Object>();
        template.setConnectionFactory(factory);

        //Json序列化配置
        // 使用Fastjson2作为值的序列化器
        FastJson2RedisSerializer<Object> fastJsonRedisSerializer = new FastJson2RedisSerializer<>(Object.class);

        // Spring的序列化
        StringRedisSerializer stringRedisSerializer = new StringRedisSerializer();
        // key采用String的序列化方式
        template.setKeySerializer(stringRedisSerializer);
        // hash的key也采用string的序列化方式
        template.setHashKeySerializer(stringRedisSerializer);
        // value的序列化方式采用的是jackson
        template.setValueSerializer(fastJsonRedisSerializer);
        // hash的value序列化方式采用jackson
        template.setHashKeySerializer(fastJsonRedisSerializer);
        template.afterPropertiesSet();
        return template;
    }
}

```

```java

/**
 * Redis使用FastJson2序列化
 *
 * @author 
 */
public class FastJson2RedisSerializer<T> implements RedisSerializer<T>
{
    /**
     * 自动识别json对象白名单配置（仅允许解析的包名，范围越小越安全）
     */
    public static final String[] JSON_WHITELIST_STR = { "org.springframework", "com.vipsoft" };

    public static final Charset DEFAULT_CHARSET = Charset.forName("UTF-8");

    static final Filter AUTO_TYPE_FILTER = JSONReader.autoTypeFilter(JSON_WHITELIST_STR);

    private Class<T> clazz;

    public FastJson2RedisSerializer(Class<T> clazz)
    {
        super();
        this.clazz = clazz;
    }

    @Override
    public byte[] serialize(T t) throws SerializationException
    {
        if (t == null)
        {
            return new byte[0];
        }
        return JSON.toJSONString(t, JSONWriter.Feature.WriteClassName).getBytes(DEFAULT_CHARSET);
    }

    @Override
    public T deserialize(byte[] bytes) throws SerializationException
    {
        if (bytes == null || bytes.length <= 0)
        {
            return null;
        }
        String str = new String(bytes, DEFAULT_CHARSET);
        return (T)JSON.parseObject(str, clazz, AUTO_TYPE_FILTER);
    }
}
```

