# ⚡ @crypto/argon2 — Memory-Hard Password Hashing for Zeta

**Port of the Rust `argon2` crate (v0.5.x). Argon2id per RFC 9106.
Pure Zeta. Memory-hard. Side-channel resistant.**

---

## 📦 Package

```
zorbs add @crypto/argon2
```

## 🔧 API

### Hash Password (raw bytes)

```zeta
let hash = hash_password(password, salt);
// 32-byte derived key (recommended params: 64MB, 3 passes, 4 lanes)
```

### Custom Parameters

```zeta
let params = Argon2Params::low_mem();  // 4MB, 2 passes
let hash = argon2id(password, salt, &params, 32);
```

### Encoded Hash (PHC String Format)

```zeta
let encoded = hash_encoded(password, salt, &params);
// $argon2id$v=19$m=65536,t=3,p=4$<salt_b64>$<hash_b64>
```

### Available Parameter Presets

| Preset | Memory | Time | Parallelism | Use Case |
|---|---|---|---|---|
| `recommended()` | 64 MB | 3 | 4 | Server-side (RFC 9106) |
| `minimum()` | 19 MB | 1 | 1 | Minimum secure |
| `low_mem()` | 4 MB | 2 | 1 | Embedded / resource-constrained |

## 📄 License

MIT OR Apache-2.0
