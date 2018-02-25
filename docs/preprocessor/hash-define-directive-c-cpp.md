---
title: "##define — dyrektywa (C/C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#define'
dev_langs:
- C++
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d06a24d969f0ae7545f1b9ec0401e098a2bcf54
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="define-directive-cc"></a>#define — dyrektywa (C/C++)
`#define` Tworzy *makro*, który jest skojarzenie identyfikatora lub identyfikatora sparametryzowane zawierające ciąg tokenu. Po zdefiniowaniu makro, kompilator może zastąpić ciąg tokenu dla każdego wystąpienia identyfikatora w pliku źródłowym.  
  
## <a name="syntax"></a>Składnia  
 `#define` *Identyfikator* *ciąg tokenu*opcjonalnych  
  
 `#define` *Identyfikator* `(` *identyfikator*opt`,`*...*  `,` *identyfikator*opt`)`*ciąg tokenu*opcjonalnych  
  
## <a name="remarks"></a>Uwagi  
 `#define` Dyrektywy powoduje, że kompilator zastępuje *ciąg tokenu* dla każdego wystąpienia *identyfikator* w pliku źródłowym. *Identyfikator* zastępuje tylko wtedy, gdy wchodzi w skład tokenu. Oznacza to *identyfikator* nie zostanie zastąpiony, jeśli występuje on w komentarza, w ciągu lub jako część identyfikatora dłużej. Aby uzyskać więcej informacji, zobacz [tokenów](../cpp/tokens-cpp.md).  
  
 *Ciąg tokenu* argument składa się z szeregu tokenów, na przykład słowa kluczowe, stałe lub kompletne instrukcje. Białe znaki muszą być rozdzielone *ciąg tokenu* z *identyfikator*. Ten biały znak nie jest uznawany za część tekst zastępczy nie jest biały znak wszystkie występującym ostatni token tekstu.  
  
 A `#define` bez *ciąg tokenu* usuwa wystąpienia *identyfikator* z pliku źródłowego. *Identyfikator* pozostaje zdefiniowany i mogą być testowane za pomocą `#if defined` i `#ifdef` dyrektywy.  
  
 Drugi formularz składni definiuje makra przypominającej funkcji z parametrami. Ten formularz przyjmuje opcjonalną listę parametrów, które muszą być ujęte w nawiasy. Po makro jest określone, każda kolejne wystąpienie *identyfikator*( *identyfikator*opcjonalnych,..., *identyfikator*opt) zostanie zastąpiony przy użyciu wersji  *ciąg tokenu* argumentu, który ma argumenty rzeczywiste zastępowane dla parametrów formalnych.  
  
 Nazwy parametrów formalnych są wyświetlane w *ciąg tokenu* do oznaczania lokalizacji, w którym są zastępowane rzeczywistymi wartościami. Każda nazwa parametru może pojawić się wiele razy w *ciąg tokenu*, i nazwy mogą pojawiać się w dowolnej kolejności. Liczba argumentów w wywołaniu musi być zgodna z liczbą parametrów w definicji makra. Rozległych Użyj nawiasów gwarantuje prawidłowo interpretowane złożonych rzeczywistych argumentów.  
  
 Parametrów formalnych na liście są oddzielone przecinkami. Nazwy na liście muszą być unikatowe i listy musi być ujęta w nawiasy. Nie może zawierać spacji można oddzielić *identyfikator* a nawiasem otwierającym. Użyj łączenia linii — umieścić ukośnik odwrotny (`\`) bezpośrednio przed znakiem nowego wiersza — długie dyrektyw wiele wierszy źródłowych. Zakres nazwy parametrów formalnych rozszerza do nowego wiersza, który kończy się *ciąg tokenu*.  
  
 W przypadku makra został zdefiniowany w drugiej formy składni, kolejne wystąpienia tekstową następuje listy argumentów wskazują wywołanie makra. Rzeczywiste argumenty, które wykonuje wystąpienia *identyfikator* w pliku źródłowym są dopasowywane do odpowiednich parametrów formalnych w definicji makra. Poszczególnych parametrów formalnych w *ciąg tokenu* który nie jest poprzedzony tworzenia ciągów (`#`), konwersji na znaki (`#@`), lub wklejania tokenu (`##`), operator lub nie następuje `##` operator, jest zastępuje odpowiednie rzeczywisty argument. Makra w rzeczywisty argument zostaną rozwinięte przed dyrektywy zastępuje parametrów formalnych. (Operatory są opisane w [operatory preprocesora](../preprocessor/preprocessor-operators.md).)  
  
 Poniższe przykłady makr z argumentami ilustrują drugiej formy `#define` składni:  
  
```  
// Macro to define cursor lines   
#define CURSOR(top, bottom) (((top) << 8) | (bottom))  
  
// Macro to get a random integer with a specified range   
#define getrandom(min, max) \  
    ((rand()%(int)(((max) + 1)-(min)))+ (min))  
```  
  
 Argumenty z efektami ubocznymi wywoływać makra powodować nieoczekiwane wyniki. Dany parametr formalny może występować więcej niż jeden raz w *ciąg tokenu*. Jeśli ten parametr formalny został zastąpiony przez wyrażenie o skutki uboczne, wyrażenie z jej efektami ubocznymi może być oceniana więcej niż jeden raz. (Zobacz przykłady w obszarze [Operator wklejania tokenu (##)](../preprocessor/token-pasting-operator-hash-hash.md).)  
  
 `#undef` Dyrektywy powoduje, że identyfikator definicji preprocesora można zapomnienia hasła. Zobacz [#undef — dyrektywa](../preprocessor/hash-undef-directive-c-cpp.md) Aby uzyskać więcej informacji.  
  
 Jeśli nazwą makra definiowanego występuje w *ciąg tokenu* (nawet wyniku innego rozwinięciu makra), nie jest rozwinięte.  
  
 Drugi `#define` dla makra o takiej samej nazwie generuje ostrzeżenie, jeśli drugi sekwencja tokenów jest taka sama jak pierwsza.  
  
 **Microsoft Specific**  
  
 Microsoft C/C++ pozwala ponownie zdefiniować makro, jeśli nowa definicja jest składniowo identyczny oryginalnej definicji. Innymi słowy dwie definicje może mieć różne nazwy parametrów. To zachowanie różni się od [!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)] C, które wymaga, aby dwie definicje lexically identyczne.  
  
 Na przykład dwa następujące makra są identyczne z wyjątkiem nazwy parametrów. [!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)] C nie zezwala na takie zmiana definicji, ale Microsoft C/C++ kompiluje go bez błędów.  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( a1 * a2 )  
```  
  
 Z drugiej strony następujących dwóch makr nie są identyczne i wygeneruje ostrzeżenie w Microsoft C/C++.  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( b1 * b2 )  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 W tym przykładzie przedstawiono `#define` dyrektywy:  
  
```  
#define WIDTH       80  
#define LENGTH      ( WIDTH + 10 )  
```  
  
 Pierwsza instrukcja definiuje identyfikator `WIDTH` jako liczba całkowita stałej 80 i definiuje `LENGTH` pod względem `WIDTH` i integer stałej 10. Każde wystąpienie `LENGTH` zastępuje (`WIDTH + 10`). Z kolei, każde wystąpienie `WIDTH + 10` zostanie zastąpiony przez wyrażenie (`80 + 10`). Nawiasy otaczające `WIDTH + 10` są ważne, ponieważ decydować interpretacji w instrukcjach, takich jak następujące:  
  
```  
var = LENGTH * 20;  
```  
  
 Staje się po przetwarzaniu wstępnym etapie instrukcji:  
  
```  
var = ( 80 + 10 ) * 20;  
```  
  
 która daje w wyniku 1800. Bez nawiasów wynikiem jest:  
  
```  
var = 80 + 10 * 20;  
```  
  
 która daje w wyniku 280.  
  
 **Microsoft Specific**  
  
 Definiowanie makr i stałe z [/D](../build/reference/d-preprocessor-definitions.md) — opcja kompilatora działa tak samo jak przy użyciu `#define` dyrektywy przetwarzania wstępnego na początku pliku. Przy użyciu opcji /D można zdefiniować maksymalnie 30 makra.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)