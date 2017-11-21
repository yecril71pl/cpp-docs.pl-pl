---
title: "Wywołania funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3f04acfe9458b8a10142ef7bc12155bc8e2a9a52
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="function-calls"></a>Wywołania funkcji
A *wywołanie funkcji* jest wyrażenie, które przekazuje kontroli i argumentów (jeśli istnieje) do funkcji i ma postać:  
  
 *wyrażenie* (*lista wyrażeń*opt)  
  
 gdzie *wyrażenie* jest nazwą funkcji lub daje w wyniku adresu funkcji i *lista wyrażeń* znajduje się lista wyrażeń (oddzielone przecinkami). Wartości tych końcowych wyrażeń są argumentami przekazywanymi do funkcji. Jeśli funkcja nie zwraca wartości, a następnie Zadeklaruj funkcją, która zwraca `void`.  
  
 Jeśli w deklaracji występuje przed wywołaniem funkcji, ale podano żadnych informacji dotyczących parametrów, argumenty niezadeklarowany po prostu przechodzą popularne konwersje arytmetyczne.  
  
> [!NOTE]
>  Wyrażenia w liście argumentów funkcji może przyjąć w dowolnej kolejności, więc argumentów, których wartości mogą zostać zmienione przez efekty uboczne z innego argumentu ma niezdefiniowane wartości. Punktu sekwencji zdefiniowane przez operator wywołania funkcji tylko gwarantuje, że wszystkie efekty uboczne w liście argumentów są oceniane przed kontrola przechodzi do wywołanej funkcji. (Należy pamiętać, że kolejność argumentów przesyłanych na stosie oddzielne sprawy.) Zobacz [punkty sekwencji](../c-language/c-sequence-points.md) Aby uzyskać więcej informacji.  
  
 Jedynym wymaganiem w żadnym wywołaniu funkcji jest, że przed nawiasów wyrażenia musi być adresu funkcji. Oznacza to, że funkcja może być wywoływana za pomocą dowolnego wyrażenia wskaźnika funkcji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono wywoływane z wywołania funkcji `switch` instrukcji:  
  
```  
int main()  
{  
    /* Function prototypes */  
  
    long lift( int ), step( int ), drop( int );  
    void work( int number, long (*function)(int i) );  
  
    int select, count;  
    .  
    .  
    .  
    select = 1;  
    switch( select )   
    {  
        case 1: work( count, lift );  
                break;  
  
        case 2: work( count, step );  
                break;  
  
        case 3: work( count, drop );  
                /* Fall through to next case */  
        default:  
                break;  
    }  
}  
  
/* Function definition */  
  
void work( int number, long (*function)(int i) )  
{  
    int i;  
    long j;  
  
    for ( i = j = 0; i < number; i++ )  
            j += ( *function )( i );  
}  
```  
  
 W tym przykładzie funkcja wywołanie w `main`,  
  
```  
work( count, lift );  
```  
  
 przekazuje zmienna całkowitoliczbowa `count`i adres funkcji `lift` funkcji `work`. Należy pamiętać, że adres funkcji jest przekazywany przez nadanie identyfikator funkcji, ponieważ identyfikator funkcji daje w wyniku wyrażenia wskaźnika. Aby korzystać z identyfikatorem funkcji w ten sposób, funkcji muszą być zadeklarowane lub zdefiniowane przed użyciem identyfikator; w przeciwnym razie identyfikator nie został rozpoznany. W tym przypadku prototyp `work` znajduje się na początku `main` funkcji.  
  
 Parametr `function` w `work` został zadeklarowany jako wskaźnik do funkcji, których jedna `int` argument i zwracanie **długi** wartość. Nawiasy otaczające nazwę parametru są wymagane; Deklaracja bez obawy, określ funkcji zwracającej wskaźnik do **długi** wartość.  
  
 Funkcja `work` wywołuje funkcję wybrane z wewnątrz **dla** pętli przy użyciu następujących wywołania funkcji:  
  
```  
( *function )( i );  
```  
  
 Jeden argument `i`, są przekazywane do wywołanej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../c-language/functions-c.md)