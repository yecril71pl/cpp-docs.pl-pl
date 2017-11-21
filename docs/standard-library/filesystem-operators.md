---
title: "&lt;System plików&gt; operatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::operator==
- FILESYSTEM/std::experimental::filesystem::operator!=
- FILESYSTEM/std::experimental::filesystem::operator<
- FILESYSTEM/std::experimental::filesystem::operator<=
- FILESYSTEM/std::experimental::filesystem::operator>
- FILESYSTEM/std::experimental::filesystem::operator>=
- FILESYSTEM/std::experimental::filesystem::operator/
- FILESYSTEM/std::experimental::filesystem::operator<<
- FILESYSTEM/std::experimental::filesystem::operator>>
dev_langs: C++
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b3587822536a6eff54b42c36b155836a9e49ab5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltfilesystemgt-operators"></a>&lt;System plików&gt; operatory
Operatory wykonać leksykalne porównanie dwóch ścieżek jako ciągi. Użyj **równoważne** funkcji, aby określić, czy dwie ścieżki (na przykład ścieżka względna i ścieżką bezwzględną) odnoszą się do tego samego pliku lub katalogu na dysku.  
  
```  
C:\root> D:\root: false  
C:\root> C:\root\sub: false  
C:\root> C:\roo: true  
```  
  
 Aby uzyskać więcej informacji, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).  
  
## <a name="operator"></a>operator==  
  
```  
bool operator==(const path& left, const path& right) noexcept;  
```  
  
 Funkcja zwraca left.native() == right.native().  
  
## <a name="operator"></a>operator!=  
  
```  
bool operator!=(const path& left, const path& right) noexcept;  
```  
  
 Funkcja zwraca! (po lewej == prawo).  
  
## <a name="operator"></a>operator<  
  
```  
bool operator<(const path& left, const path& right) noexcept;  
```  
  
 Funkcja zwraca left.native() < right.native().  
  
## <a name="operator"></a>operator<=  
  
```  
bool operator<=(const path& left, const path& right) noexcept;  
```  
  
 Funkcja zwraca! (prawo \< po lewej stronie).  
  
## <a name="operator"></a>operator >  
  
```  
bool operator>(const path& left, const path& right) noexcept;  
```  
  
 Funkcja zwraca prawo \< po lewej stronie.  
  
## <a name="operator"></a>operator > =  
  
```  
bool operator>=(const path& left, const path& right) noexcept;  
```  
  
 Funkcja zwraca! (po lewej stronie < prawo).  
  
## <a name="operator"></a>operator /  
  
```  
path operator/(const path& left, const path& right);
```  
  
 Funkcja wykonuje:  
  
```  
basic_string<Elem, Traits> str;  
path ans = left;  
return (ans /= right);
```  
  
## <a name="operator"></a>Operator <<  
  
```  
template <class Elem, class Traits>  
basic_ostream<Elem, Traits>& operator<<(basic_ostream<Elem, Traits>& os, const path& pval);
```  
  
 Funkcja zwraca os << pval.string\<elementu, cech > ().  
  
## <a name="operator"></a>operator >>  
  
```  
template <class Elem, class Traits>  
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```  
  
 Funkcja wykonuje:  
  
```  
basic_string<Elem, Traits> str;  
is>> str;  
pval = str;  
return (is);
```  
  
## <a name="see-also"></a>Zobacz też  
 [PATH — klasa (standardowa biblioteka C++)](../standard-library/path-class.md)   
 [Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md)   
 [\<FileSystem >](../standard-library/filesystem.md)

