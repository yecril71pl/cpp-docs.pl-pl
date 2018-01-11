---
title: "this, wskaźnik | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: this_cpp
dev_langs: C++
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 814e7518c6ed7052abc93b9e4705be93172b1e7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="this-pointer"></a>this — wskaźnik
**To** wskaźnika jest dostępny tylko w ramach funkcji niestatycznego elementu członkowskiego wskaźnik **klasy**, `struct`, lub **Unii** typu. Wskazuje obiekt, dla której wywołano tę funkcję elementu członkowskiego. Statyczne funkcje Członkowskie nie mają **to** wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      this   
this->member-identifier  
```  
  
## <a name="remarks"></a>Uwagi  
 Obiekt **to** wskaźnik nie jest częścią obiektu; nie zostanie uwzględniony w wyniku `sizeof` instrukcji w obiekcie. Zamiast tego niestatycznej funkcji członkowskiej wywołanego obiektu adres obiektu jest przekazywany przez kompilator jako ukryty argument do funkcji. Na przykład następujące wywołanie funkcji:  
  
```  
myDate.setMonth( 3 );  
```  
  
 może zostać zinterpretowany w ten sposób:  
  
```  
setMonth( &myDate, 3 );  
```  
  
 Adres obiektu są dostępne za pośrednictwem funkcji członkowskiej jako **to** wskaźnika. Większość zastosowań **to** są niejawne. Jest prawnych, chociaż jest to konieczne, jawnie używać **to** podczas odwoływania się do elementów członkowskich klasy. Na przykład:  
  
```  
void Date::setMonth( int mn )  
{  
   month = mn;            // These three statements  
   this->month = mn;      // are equivalent  
   (*this).month = mn;  
}  
```  
  
 Wyrażenie `*this` jest najczęściej używany do zwrócenia bieżącego obiektu z funkcją członkowską:  
  
```  
return *this;  
```  
  
 **To** wskaźnika jest również używany do ochrony przed odwołanie do samego siebie:  
  
```  
if (&Object != this) {  
// do not execute in cases of self-reference  
```  
  
> [!NOTE]
>  Ponieważ **to** wskaźnika jest niemodyfikowalnymi, przydziały w celu **to** nie są dozwolone. Przypisania, aby dozwolone wcześniejszych implementacji C++ **to**.  
  
 Czasami **to** wskaźnika jest używana bezpośrednio — na przykład można manipulować danymi odwołań do siebie struktury, gdy wymagany jest adres bieżącego obiektu.  
  
## <a name="example"></a>Przykład  
  
```  
// this_pointer.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
  
class Buf   
{  
public:  
    Buf( char* szBuffer, size_t sizeOfBuffer );  
    Buf& operator=( const Buf & );  
    void Display() { cout << buffer << endl; }  
  
private:  
    char*   buffer;  
    size_t  sizeOfBuffer;  
};  
  
Buf::Buf( char* szBuffer, size_t sizeOfBuffer )  
{  
    sizeOfBuffer++; // account for a NULL terminator  
  
    buffer = new char[ sizeOfBuffer ];  
    if (buffer)  
    {  
        strcpy_s( buffer, sizeOfBuffer, szBuffer );  
        sizeOfBuffer = sizeOfBuffer;  
    }  
}  
  
Buf& Buf::operator=( const Buf &otherbuf )   
{  
    if( &otherbuf != this )   
    {  
        if (buffer)  
            delete [] buffer;  
  
        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;   
        buffer = new char[sizeOfBuffer];  
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );  
    }  
    return *this;  
}  
  
int main()  
{  
    Buf myBuf( "my buffer", 10 );  
    Buf yourBuf( "your buffer", 12 );  
  
    // Display 'my buffer'  
    myBuf.Display();  
  
    // assignment opperator  
    myBuf = yourBuf;  
  
    // Display 'your buffer'  
    myBuf.Display();  
}  
```  
  
```Output  
my buffer  
your buffer  
```  
  
## <a name="type-of-the-this-pointer"></a>Ten typ wskaźnika  
 **To** typu wskaźnika można modyfikować w deklaracji funkcji **const** i `volatile` słów kluczowych. Aby zadeklarować funkcji jako zawierający atrybuty jednego lub więcej z następujących słów kluczowych, Dodaj słowa po liście argumentów funkcji.  
  
 Rozważmy następujący przykład:  
  
```  
// type_of_this_pointer1.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 Poprzedni kod deklaruje funkcją członkowską `X`, w którym **to** wskaźnika jest traktowany jako **const** wskaźnik do **const** obiektu. Kombinacje *cv mod listy* opcje mogą być używane, ale zawsze modyfikować wskazywanego przez obiekt **to**, a nie **to** wskaźnika samej siebie. W związku z tym następujące oświadczenie deklaruje funkcja `X`; **to** wskaźnika jest **const** wskaźnik do **const** obiektu:  
  
```  
// type_of_this_pointer2.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 Typ **to** w elemencie członkowskim funkcja jest opisana przy użyciu następującej składni, gdzie *cv kwalifikator listy* jest określana na podstawie deklarator funkcji Członkowskich i może być **const**lub **volatile** (lub oba), a *typu klasy* jest nazwa klasy:  
  
 *Typ klasy [cv kwalifikator list]*  **\* const to**   
  
 Innymi słowy **to** jest zawsze stałą wskaźnika; nie może zostać przypisany.  **Const** lub `volatile` kwalifikatory używany w deklaracji funkcji Członkowskich dotyczą wskazywana przez wystąpienie klasy **to** w zakresie tej funkcji.  
  
 W poniższej tabeli przedstawiono więcej informacji na temat Modyfikatory te działania.  
  
### <a name="semantics-of-this-modifiers"></a>Semantyka tej modyfikatorów  
  
|Modyfikator|Znaczenie|  
|--------------|-------------|  
|**const**|Nie można zmienić elementu członkowskiego danych; Nie można wywołać funkcji elementów członkowskich, które nie są **const**.|  
|`volatile`|Dane elementów członkowskich są ładowane z pamięci zawsze, gdy jest on dostępny; Wyłącza optymalizacje niektórych.|  
  
 Błąd do przekazania **const** obiektu do funkcji członkowskiej, która nie jest **const**. Podobnie, występuje błąd do przekazania `volatile` obiektu do funkcji członkowskiej, która nie jest `volatile`.  
  
 Funkcje Członkowskie zadeklarowany jako **const** nie można zmienić elementu członkowskiego danych — w takie funkcje **to** wskaźnika jest wskaźnikiem do **const** obiektu.  
  
> [!NOTE]
>  Konstruktory i destruktory nie można zadeklarować jako **const** lub `volatile`. Jednak może być wywołana na **const** lub `volatile` obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 