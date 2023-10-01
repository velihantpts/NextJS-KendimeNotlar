* Next JS'te iki tür sayfalar arası geçiş için iki yöntem mevcut;
### 1. <Link> Componenti
Link componenti HTML'deki `<a>` etiketinin daha gelişmiş, genişletişmiş hali diyebiliriz. `import Link from 'next/link`  sayfaya dahil ettikten sonra aşagığdaki gibi kullanabiliriz
```
import Link from 'next/link'
 
export default function Page() {
  return <Link href="/dashboard">Dashboard</Link>
}
```
href'e hangi path'e gitmek istiyorsak o adresi verebiliriz.
Her zaman bu kadar basit yönlendirmeler yapmak istemeyebiliriz, bazı zamanlar  dinamik yönlendirme yaparak daha gelişmiler yapılar isteriz.
```
import Link from 'next/link'
 
export default function PostList({ posts }) {
  return (
    <ul>
      {posts.map((post) => (
        <li key={post.id}>
          <Link href={`/blog/${post.slug}`}>{post.title}</Link>
        </li>
      ))}
    </ul>
  )
}
```
Yukarıda örnekteki gibi blog postlarının bir listesini yapabiliriz. Her Link'te ilgili blog pathine gitmemizi sağlar
* usePathname ile bir path'in aktifliğini kontrol edebiliriz
```
'use client'
 
import { usePathname } from 'next/navigation'
import Link from 'next/link'
 
export function Links() {
  const pathname = usePathname()
 
  return (
    <nav>
      <ul>
        <li>
          <Link className={`link ${pathname === '/' ? 'active' : ''}`} href="/">
            Home
          </Link>
        </li>
        <li>
          <Link
            className={`link ${pathname === '/about' ? 'active' : ''}`}
            href="/about"
          >
            About
          </Link>
        </li>
      </ul>
    </nav>
  )
}
```
### 2. useRouter hook'u
useRouter hooku programlanabilir routing yapmamıza olanak sağlar. `import { useRouter } from 'next/navigation'` şeklinde dahil edip kullanılabiliriz.
```
'use client'
 
import { useRouter } from 'next/navigation'
 
export default function Page() {
  const router = useRouter()
 
  return (
    <button type="button" onClick={() => router.push('/dashboard')}>
      Dashboard
    </button>
  )
}

```
### Next JS'de routing mantığı nasıl çalışır ?
* Prefetching
  Bu iki yolla gerçekleşir. Birincisi `<Link>` componenti kullanıcının gördüğü alandaki veya kaydırma sırasında görünen rotaları ön getirme işlemi gerçekleştirir. Burada iki adet işlem vardır statik ve dinamik, statik
  tümm rotaları ön belleği alırken dinamik ise belirli koşullarda ön belleğe alır.
  ikincisi ise router.prefetch() ile manuel şekilde yapılır. 
* Caching
  Next.js kullanıcın gezindiği sayfaları cache'e atarak sunucuya tekrar istek yollamaz, bunun yerine cacheden verileri çeker.
* Partial Rendering
  Next.js'de routing tüm sayfanın render edilmesinden ziyade değişen kısımların renderlanması mantığına dayanır. Bu hem performans hem de hız anlamında avantajlar sunmaktadır. Eğer `partial rendering` kavramı kulalnılmasaydı
  kullanıcı her sayfayı yenilediğinde veya sayfa geçişleri sırasında tüm öğeler baştan renderlanacağı için perfermons kayıplarına neden olurdu.
![image](https://github.com/velihantpts/NextJS-KendimeNotlar/assets/56006189/05826744-b74b-40c8-8401-dc1e675ac412)

