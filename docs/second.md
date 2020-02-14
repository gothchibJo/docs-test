Это второй файл в корневой директории с документацией.

Создан в целях проверки, куда его прилепит ридзедок.

Вот и посмотрим...

```
code
    block
```

```javascript
class Cache extends Map {

  constructor(ttl) {
    if (ttl <= 0) throw new Error('TTL should be a positive value');
    super();
    this.ttl = ttl;
  }

  set(key, value) {
    if (this.ttl) setTimeout(() => super.delete(key), this.ttl);
    return super.set(key, value);
  }

  getOut(key) {
    return [super.get(key), super.delete(key)][0];
  }
}

module.exports = Cache;

```

