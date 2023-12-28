## example

```tsx
axios.get('http://xxxxxx', { responseType: 'blob' }).then((response) => {
  const blob = new Blob([response.data], { type: response.data.type })
  
  // 创建一个临时链接
  const url = URL.createObjectURL(blob)
  
  // 创建一个<a>元素，设置其href属性为Blob链接，触发点击事件实现下载
  const link = document.createElement('a')
  link.href = url
  link.download = 'filename' // 设置下载文件的文件名和扩展名
  document.body.appendChild(link)
  link.click()
  
  // 释放临时链接和<a>元素
  URL.revokeObjectURL(url)
  document.body.removeChild(link)
})
```
