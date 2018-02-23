---
title: "Operatory pośrednie i operatorów adresu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d65a380194e5634d5873e9b060c49096197e48f2
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="indirection-and-address-of-operators"></a>Operatory pośrednie i „Address-of”

Jednoargumentowy operator pośredni (__&#42;__) uzyskuje dostęp do wartości pośrednio, za pomocą wskaźnika. Argument musi być typu wskaźnika. Wynik operacji jest wartością adresowaną przez operand; czyli wartość pod adresem, na który wskazuje operand. Typ wyniku jest typem adresowanym przez operand.

Wynik operator pośredni jest *typu* Jeśli operand jest typu *wskaźnika na typ*. Jeśli operand wskazuje funkcję, wynik jest oznaczeniem funkcji. Wskazuje na obiekt, wynikiem jest l-wartość, która określa obiekt.

Jeśli wartość wskaźnika nie jest prawidłowe, wynikiem operator pośredni jest niezdefiniowany. Są to najbardziej typowe warunki, które unieważnienie wartość wskaźnika:

- Wskaźnik jest pustym wskaźnikiem.

- Wskaźnik Określa adres obiektu po zakończeniu jego okres istnienia (na przykład obiekt, który został usunięty poza zakresem lub które zostały cofnięciu przydziału) w czasie odwołania.

- Wskaźnik określa adres, który jest nieodpowiednio wyrównany dla typu wskazywanego obiektu.

- Wskaźnik określa adres nieużywany przez program wykonujący.

Jednoargumentowy operator address-of (**&**) zapewnia adres jej argument. Operand musi być albo lewostronnie określa obiekt, który nie jest zadeklarowany jako __zarejestrować__ i nie jest polem bitowym ani wynik jednoargumentowy __&#42;__ operator lub tablicy wyłuskania ( __&#91; &#93;__ ) — operator lub oznaczeniem funkcji. Wynik jest typu *wskaźnika na typ* dla argumentu operacji typu *typu*.

Jeśli argument jest wynikiem jednoargumentowy __&#42;__ operatora, żaden operator nie jest obliczane i wynikiem jest tak, jakby zarówno zostały pominięte. Wynik nie jest l-wartością i ograniczenia dotyczące operatorów nadal stosowane. Jeśli argument jest wynikiem __&#91; &#93;__ operatora, ani  __&__  , ani operatora jednoargumentowego __&#42;__ określone przez  __&#91; &#93;__  operator jest obliczane. Wynik zawiera ten sam efekt co usuwanie  __&__  operatora i zmianę __&#91; &#93;__ operatora  __+__  operatora. W przeciwnym razie wynikiem jest wskaźnik do obiektu lub funkcja wskazywany przez argument.


## <a name="examples"></a>Przykłady

W poniższych przykładach użyto tych wspólnych deklaracji:

```C
int *pa, x;
int a[20];
double d;
```

Ta instrukcja używa address-of — operator (**&**) można pobrać adresu szóstego element tablicy `a`. Wynik jest przechowywany w zmiennej wskaźnikowej `pa`:

```C  
pa = &a[5];
```

Operator pośredni (__&#42;__) służy w tym przykładzie, aby uzyskać dostęp do `int` wartość pod adresem przechowywane w `pa`. Wartość jest przypisany do zmiennej całkowitą `x`:

```C
x = *pa;
```

W tym przykładzie pokazano, że wynik zastosowania operator bezpośredni adres `x` jest taka sama jak `x`:

```C
assert( x == *&x );
```

W tym przykładzie przedstawiono sposoby równoważne deklarowanie wskaźnika do funkcji:

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```  

Gdy deklarowana jest funkcja `roundup`, deklarowane i inicjowane są dwa wskaźniki do `roundup`. Pierwszy wskaźnik `proundup` jest inicjowany jedynie za pomocą nazwy funkcji, podczas gdy drugi `pround` używa operatora address-of przy inicjalizacji. Inicjalizacje są równoważne.

## <a name="see-also"></a>Zobacz także

[Operator bezpośredni: &#42;](../cpp/indirection-operator-star.md)  
[Operator Address-of: &](../cpp/address-of-operator-amp.md)  
