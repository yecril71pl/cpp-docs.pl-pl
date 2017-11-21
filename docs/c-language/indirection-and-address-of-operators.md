---
title: "Operatory pośrednie i operatorów adresu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- address-of operator (&)
- '* operator'
- operators [C++], address-of
- ampersand operator (&)
- '* operator, indirection operator'
- addresses [C++], indirection
- addresses [C++]
- indirection operator
- '& operator, address-of operator'
- null pointers [C++]
- '* operator, address-of operator'
- operators [C++], indirection
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 85d2510658bdf534f25ccc3efc29c88da1c93eff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="indirection-and-address-of-operators"></a>Operatory pośrednie i „Address-of”
Operator pośredni (**\***) uzyskuje dostęp do wartości pośrednio, za pomocą wskaźnika. Operand musi być wartością wskaźnika. Wynik operacji jest wartością adresowaną przez operand; czyli wartość pod adresem, na który wskazuje operand. Typ wyniku jest typem adresowanym przez operand.  
  
 Jeśli operand wskazuje funkcję, wynik jest oznaczeniem funkcji. Jeśli wskazuje on lokalizację magazynu, wynikiem jest l-wartość opisująca lokalizację magazynu.  
  
 Jeśli wartość wskaźnika jest nieprawidłowy, wynikiem jest niezdefiniowany. Następująca lista zawiera niektóre z najbardziej typowych warunków, które unieważniają wartość wskaźnika.  
  
-   Wskaźnik jest pustym wskaźnikiem.  
  
-   Wskaźnik określa adres lokalnego elementu, który nie jest widoczny w momencie odwołania.  
  
-   Wskaźnik określa adres, który jest nieodpowiednio wyrównany dla typu wskazywanego obiektu.  
  
-   Wskaźnik określa adres nieużywany przez program wykonujący.  
  
 Address-of — operator (**&**) zapewnia adres jej argument. Argument address-of — operator może być oznaczeniem funkcji lub l wartość, która określa obiekt, który nie jest polem bitowym i nie jest zadeklarowany z **zarejestrować** Specyfikator klasy magazynowania.  
  
 Wynik operacji adresu jest wskaźnikiem do operandu. Typ adresowany przez wskaźnik jest typem operandu.  
  
 Operator address-of można stosować tylko do zmiennych o typie podstawowym, strukturalnym lub unii, które zostały zadeklarowane na poziomie pliku lub do indeksowanych odwołań do tablic. W tych wyrażeniach wyrażenie stałe, które nie zawiera operatora address-of może być dodane lub odjęte od wyrażenia adresu.  
  
## <a name="examples"></a>Przykłady  
 W poniższych przykładach użyto tych deklaracji:  
  
```  
int *pa, x;  
int a[20];  
double d;  
```  
  
 Ta instrukcja używa operatora address-of:  
  
```  
pa = &a[5];  
```  
  
 Address-of — operator (**&**) ma adres szóstego element tablicy `a`. Wynik jest przechowywany w zmiennej wskaźnika `pa`.  
  
```  
x = *pa;  
```  
  
 Operator pośredni (**\***) służy w tym przykładzie, aby uzyskać dostęp do `int` wartość pod adresem przechowywane w `pa`. Wartość jest przypisywana do zmiennej całkowitej `x`.  
  
```  
if( x == *&x )  
    printf( "True\n" );  
```  
  
 Ten przykład drukuje wyraz `True`, pokazując, że wynik zastosowania operatora pośredniego do adresu `x` jest taki sam jak `x`.  
  
```  
int roundup( void );     /* Function declaration */  
  
int  *proundup  = roundup;  
int  *pround  = &roundup;  
```  
  
 Gdy deklarowana jest funkcja `roundup`, deklarowane i inicjowane są dwa wskaźniki do `roundup`. Pierwszy wskaźnik `proundup` jest inicjowany jedynie za pomocą nazwy funkcji, podczas gdy drugi `pround` używa operatora address-of przy inicjalizacji. Inicjalizacje są równoważne.  
  
## <a name="see-also"></a>Zobacz też  
 [Operator bezpośredni: *](../cpp/indirection-operator-star.md)   
 [Operator Address-of: &](../cpp/address-of-operator-amp.md)