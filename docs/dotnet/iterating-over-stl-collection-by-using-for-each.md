---
title: Iterowanie przez standardową kolekcję bibliotek C++ przy użyciu dla każdego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DTL collections, iterating over
ms.assetid: 9358ca29-b982-4a19-bbfd-bef50fe66c9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 92934e3f00bb34e6adfe101b0fea7abbe03600c2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383199"
---
# <a name="iterating-over-c-standard-library-collection-by-using-for-each"></a>Iterowanie przez standardową kolekcję bibliotek C++ przy użyciu dla każdego

`for each` — Słowo kluczowe może służyć do iteracji po kolekcji standardowej biblioteki języka C++.

## <a name="all-platforms"></a>Wszystkie platformy

Kolekcja standardowej biblioteki języka C++ jest także znana jako *kontenera*. Aby uzyskać więcej informacji, zobacz [standardowych kontenerów biblioteki języka C++](../standard-library/stl-containers.md).

## <a name="examples"></a>Przykłady

Poniższy przykład kodu wykorzystuje `for each` Iterowanie [ \<mapy >](../standard-library/map.md).

```cpp
// for_each_stl.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
using namespace std;

int main() {
   int retval  = 0;
   map<string, int> months;

   months["january"] = 31;
   months["february"] = 28;
   months["march"] = 31;
   months["april"] = 30;
   months["may"] = 31;
   months["june"] = 30;
   months["july"] = 31;
   months["august"] = 31;
   months["september"] = 30;
   months["october"] = 31;
   months["november"] = 30;
   months["december"] = 31;

   map<string, int> months_30;

   for each( pair<string, int> c in months )
      if ( c.second == 30 )
         months_30[c.first] = c.second;

   for each( pair<string, int> c in months_30 )
      retval++;

   cout << "Months with 30 days = " << retval << endl;
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Months with 30 days = 4
```

## <a name="example"></a>Przykład

Poniższy przykład kodu używa odniesienie const (`const&`) zmiennej iteracji za pomocą kontenerów standardowej biblioteki języka C++. Można użyć odwołania (`&`) jako zmienna iteracji w kolekcji dowolnego typu, które mogą być deklarowane jako *T*`&`.

```cpp
// for_each_stl_2.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
using namespace std;

int main() {
   int retval = 0;

   vector<int> col(3);
   col[0] = 10;
   col[1] = 20;
   col[2] = 30;

   for each( const int& c in col )
      retval += c;

   cout << "retval: " << retval << endl;
}
```

### <a name="output"></a>Dane wyjściowe

```Output
retval: 60
```

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Nie ma żadnych uwag specyficznych dla platformy, informacje o tej funkcji.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: **/ZW**

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Nie ma żadnych uwag specyficznych dla platformy, informacje o tej funkcji.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora:   **/CLR**

## <a name="see-also"></a>Zobacz też

[for each, in](../dotnet/for-each-in.md)<br/>
[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)