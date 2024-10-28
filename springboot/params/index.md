## 在 Spring MVC 中，路径参数、URL 参数（查询参数）和请求体参数是常用的三种传参方式

### 1. 路径参数（Path Variable）

- **描述**：路径参数通常用于唯一标识资源，例如 `/collections/35` 中的 `35` 表示某个特定的集合 ID。
- **使用方式**：通过 `@PathVariable` 注解来获取路径参数。
- **请求示例**：`GET /collections/35`

```java
@GetMapping("/collections/{id}")
public ResponseEntity<Collection> getCollectionById(@PathVariable Long id) {
   Collection collection = collectionService.findById(id);
   return collection != null ? ResponseEntity.ok(collection) : ResponseEntity.notFound().build();
}
```

### 2. URL 参数（Query Parameter）
- **描述**：URL 参数（也叫查询参数）通常附加在 URL 的末尾，用于过滤、排序或分页等操作。例如：/collections?type=special&limit=10。

- **使用方式**：通过 @RequestParam 注解来获取查询参数。

- **请求示例**：GET /collections?type=special&limit=10

```java
@GetMapping("/collections")
public ResponseEntity<List<Collection>> getCollections(
        @RequestParam(required = false) String type,
        @RequestParam(defaultValue = "10") int limit) {
    List<Collection> collections = collectionService.findByTypeAndLimit(type, limit);
    return collections.isEmpty() ? ResponseEntity.noContent().build() : ResponseEntity.ok(collections);
}
```
### 3. 请求体参数（Body Parameter）
- **描述**：请求体参数用于传递更复杂的数据（例如 JSON、XML 格式），通常在 POST、PUT 请求中使用，适用于创建或更新资源。

- **使用方式**：通过 @RequestBody 注解来获取请求体参数。

- **请求示例**：POST /collections，请求体内容为 JSON 格式：
  ```json
  {
    "name": "New Collection",
    "description": "This is a new collection."
  }
  ```
```java
  @PostMapping("/collections")
public ResponseEntity<Collection> createCollection(@RequestBody Collection newCollection) {
    Collection createdCollection = collectionService.save(newCollection);
    return ResponseEntity.status(HttpStatus.CREATED).body(createdCollection);
}
```
## 总结
- **路径参数**：用来唯一标识资源，写在 URL 路径中。

- **URL 参数**：用来传递可选参数或筛选信息，写在 URL 的查询字符串中。

- **请求体参数**：用来传递复杂数据，通常在请求体中传递 JSON 等格式的数据
