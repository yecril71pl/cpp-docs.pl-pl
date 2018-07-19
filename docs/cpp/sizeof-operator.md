---
title: sizeof, Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- sizeof_cpp
dev_langs:
- C++
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58724d2e17947c69d1aaf2ed0af66137fe20cc74
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947782"
---
# <a name="sizeof-operator"></a>sizeof — operator
Zwraca rozmiar swojego operandu w odniesieniu do rozmiaru typu **char**.  
  
> [!NOTE]
>  Aby uzyskać informacje o `sizeof ...` operatora, zobacz [wielokropki i szablony Wariadyczne](../cpp/ellipses-and-variadic-templates.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
sizeof unary-expression  
sizeof  ( type-name )  
```  
  
## <a name="remarks"></a>Uwagi  
 Wynik **sizeof** operator ma typ `size_t`, typem całkowitym, zdefiniowane w dołączanym pliku \<stddef.h >. Ten operator umożliwia Unikaj określania ilości danych zależnych od maszyny w swoich programach.  
  
 Argument operacji do **sizeof** może być jedną z następujących czynności:  
  
-   Nazwa typu. Aby użyć **sizeof** nazwą typu, nazwa musi być ujęte w nawiasy.  
  
-   Wyrażenie. Gdy jest używana z wyrażeniem, **sizeof** można określić, z lub bez nawiasów. Wyrażenie nie jest oceniany.  
  
 Gdy **sizeof** operator jest stosowany do obiektu typu **char**, jego daje 1. Gdy **sizeof** operator jest stosowany do tablicy, jego daje całkowita liczba bajtów w tej tablicy, a nie rozmiar wskaźnika reprezentowanego przez identyfikator tablicy. Aby uzyskać rozmiar wskaźnika reprezentowanego przez identyfikator tablicy, przekaż go jako parametr do funkcji, która używa **sizeof**. Na przykład:  
  
## <a name="example"></a>Przykład  
  
```cpp 
#include <iostream>  
using namespace std;  
  
size_t getPtrSize( char *ptr )  
{  
   return sizeof( ptr );  
}  
  
int main()  
{  
   char szHello[] = "Hello, world!";  
  
   cout  << "The size of a char is: "  
         << sizeof( char )  
         << "\nThe length of " << szHello << " is: "  
         << sizeof szHello  
         << "\nThe size of the pointer is "  
         << getPtrSize( szHello ) << endl;  
}  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```Output  
The size of a char is: 1  
The length of Hello, world! is: 14  
The size of the pointer is 4  
```  
  
 Gdy **sizeof** operator jest stosowany do **klasy**, **struktury**, lub **Unii** typu, wynik jest liczbą bajtów w obiekcie, który Typ, a także wszelkie dopełnienie, które dodano do wyrównania elementów członkowskich na granicach słów. Wynik nie musi koniecznie odpowiadać wielkości obliczonej przez dodanie pamięci wymaganej poszczególnych elementów członkowskich. [/ZP](../build/reference/zp-struct-member-alignment.md) — opcja kompilatora i [pakiet](../preprocessor/pack.md) pragma wpływają na granicach wyrównanie dla elementów członkowskich.  
  
 **Sizeof** operator nigdy nie daje 0, nawet w przypadku pustą klasę.  
  
 **Sizeof** nie można używać operatora z następujących argumentów:  
  
-   Funkcje. (Jednak **sizeof** mogą być stosowane do wskaźników do funkcji.)  
  
-   Nieco pola.  
  
-   Niezdefiniowany klasy.  
  
-   Typ **void**.  
  
-   Dynamicznie przydzielane tablic.  
  
-   Tablice zewnętrznych.  
  
-   Niekompletne typy.  
  
-   Nazwy w nawiasach niekompletnych typów.  
  
 Gdy **sizeof** operator jest stosowany do odwołania, wynik jest taki sam tak, jakby **sizeof** były stosowane do samego obiektu.  
  
 Jeśli tablica bez określonego rozmiaru jest ostatnim elementem struktury, **sizeof** operator zwraca rozmiar struktury bez tablicy.  
  
 **Sizeof** operator jest często używany do Oblicz liczbę elementów w tablicy za pomocą wyrażenia formularza:  
  
```cpp 
sizeof array / sizeof array[0]  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)