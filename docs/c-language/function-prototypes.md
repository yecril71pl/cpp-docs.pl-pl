---
title: Prototypy funkcji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- function prototypes
- function return types, function prototypes
- data types [C], function return types
- functions [C], return types
- prototypes [C++], function
ms.assetid: d152f8e6-971e-432c-93ca-5a91400653c2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea02b5b3bb1517623a0c3fc67a752d203f81c5a8
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="function-prototypes"></a>Prototypy funkcji
Deklaracja funkcji poprzedza definicji funkcji i określa nazwę, typ zwracany Klasa magazynu i inne atrybuty funkcji. Jako prototyp deklaracji funkcji należy również określić typy i identyfikatory dla argumentów funkcji.  
  
## <a name="syntax"></a>Składnia  
 `declaration`:  
 *Specyfikatory deklaracji atrybutu seq* opt*init deklarator listy* opt**;**  
  
 /\* *Atrybut seq* opt jest Specific Microsoft * /  
  
 *Specyfikatory deklaracji*:  
 *Specyfikatory deklaracji Specyfikator klasy magazynu* opcjonalnych  
  
 *Specyfikatory deklaracji specyfikatora typu* opcjonalnych  
  
 *Specyfikatory deklaracji kwalifikator typu* opcjonalnych  
  
 *init-declarator-list*:  
 *init-declarator*  
  
 *init — deklarator — lista***,***init deklarator*   
  
 *init-declarator*:  
 *declarator*  
  
 *deklarator = inicjatora*  
  
 `declarator`:  
 *wskaźnik* opt*bezpośrednio deklarator*  
  
 *deklarator bezpośrednio*: /\* deklarator funkcji \*/  
 *deklarator bezpośrednio***(***listy parametrów typu***)** / * nowy styl deklarator       \*/  
  
 *deklarator bezpośrednio***(***listy identyfikatorów* opt**)** / * przestarzały styl deklarator     \*/  
  
 Prototyp ma tego samego formularza jako definicji funkcji, z wyjątkiem, że jest zakończona średnikiem bezpośrednio po nawiasie zamykającym i w związku z tym ma treść nie. W obu przypadkach zwracany typ należy uzgodnić z zwracany typ określony w definicji funkcji.  
  
 Prototypy funkcji są ważne następujące zastosowania:  
  
-   Określają typ zwracany dla funkcji zwracających typów innych niż `int`. Chociaż funkcje, które zwracają `int` wartości nie wymagają prototypy, zaleca się prototypów.  
  
-   Bez ukończenia prototypy konwersje standardowe zostały wprowadzone, ale nie są podejmowane próby do sprawdzenia typu lub liczbą argumentów z liczbą parametrów.  
  
-   Prototypy są używane do zainicjowania wskaźniki do funkcji zdefiniowaniem tych funkcji.  
  
-   Lista parametrów służy do sprawdzania zgodności argumentów w wywołaniu funkcji z parametrami w definicji funkcji.  
  
 Przekonwertowana typ każdego parametru określa interpretacji argumenty, które powoduje wywołanie funkcji na stosie. Niezgodność typu argumentu i parametr może spowodować argumenty na stosie, aby zostać błędnie zinterpretowane. Na przykład na komputerze 16-bitowych, jeśli wskaźnik 16-bitowych jest przekazywany jako argument, następnie zadeklarowany jako **długi** parametru pierwszy 32-bitowy na stosie będą interpretowane jako **długi** parametru. Ten błąd stwarza problemy nie tylko z **długi** parametru, ale wszystkie parametry, które po nim. Przez zadeklarowanie prototypy funkcji pełną dla wszystkich funkcji, można wykrywać błędy tego typu.  
  
 Prototyp ustanawia atrybuty funkcji, dzięki czemu można sprawdzić wywołania funkcji, które poprzedzać jego definicji (lub wystąpić w innych plikach źródłowych) typ argumentu i niezgodności zwracanego typu. Na przykład jeśli określisz **statycznych** Specyfikator klasy magazynu w prototyp, należy także określić **statycznej** klasy magazynu w definicji funkcji.  
  
 Zakończenie deklaracji parametrów (`int a`) można łączyć z deklaratory abstrakcyjne języka (`int`) w tej samej deklaracji. Na przykład następujące oświadczenie jest dozwolony:  
  
```  
int add( int a, int );  
```  
  
 Prototyp może zawierać typ i identyfikator dla każdego wyrażenie, które jest przekazywany jako argument. Jednak takie identyfikatory mają zakres tylko do końca deklaracji. Prototyp można również odzwierciedlają fakt, że liczba argumentów jest zmienna lub czy są przekazywane bez argumentów. Bez tych listy niezgodności może nie są ujawniane, dlatego kompilator nie może wygenerować komunikaty diagnostyczne ich dotyczących. Zobacz [argumenty](../c-language/arguments.md) Aby uzyskać więcej informacji na temat sprawdzania typu.  
  
 Zakres prototypu w kompilatorze C firmy Microsoft jest standardem ANSI teraz podczas kompilowania za pomocą /Za — opcja kompilatora. Oznacza to, że w przypadku `struct` lub **Unii** znaczniku prototyp, tag jest wprowadzana w tym zakresie, a nie w zakresie globalnym. Na przykład podczas kompilowania za pomocą /Za zgodność ANSI, nigdy nie można wywołać tej funkcji bez uzyskiwania błąd niezgodności typów:  
  
```  
void func1( struct S * );  
```  
  
 Aby rozwiązać problem kodu, zdefiniuj lub zadeklarować `struct` lub **Unii** w zakresie globalnym przed prototypu funkcji:  
  
```  
struct S;  
void func1( struct S * );  
```  
  
 W obszarze /Ze tag wprowadzona w zakresie globalnym.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../c-language/functions-c.md)