---
title: bad_alloc — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- new/std::bad_alloc
dev_langs:
- C++
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 571885410363aee55d15e68b81ba4fd9e2b8e54b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705591"
---
# <a name="badalloc-class"></a>bad_alloc — Klasa

Klasa opisuje wyjątek generowany, aby wskazać, że żądanie alokacji nie powiodła się.

## <a name="syntax"></a>Składnia

```cpp
class bad_alloc : public exception {
    bad_alloc();
virtual ~bad_alloc();

};
```

## <a name="remarks"></a>Uwagi

Wartość zwrócona przez obiekt `what` jest ciągiem C zdefiniowanych w implementacji. Żadna z funkcji elementu członkowskiego generuje żadnych wyjątków.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<nowe >

**Namespace:** standardowe

## <a name="example"></a>Przykład

```cpp
// bad_alloc.cpp
// compile with: /EHsc
#include<new>
#include<iostream>
using namespace std;

int main() {
   char* ptr;
   try {
      ptr = new char[(~unsigned int((int)0)/2) - 1];
      delete[] ptr;
   }
   catch( bad_alloc &ba) {
      cout << ba.what( ) << endl;
   }
}
```

## <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
bad allocation
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<nowe >

## <a name="see-also"></a>Zobacz też

[exception, klasa](../standard-library/exception-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
