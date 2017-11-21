---
title: "Rejestrator ALT i Nauer formularz Backus tworzą składni (BNF) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- BNF notation
- Backus Nauer Form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6ff141818e05f9b5b36b6d0cfc5a58170fa97ab0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="understanding-backus-nauer-form-bnf-syntax"></a>Opis Nauer formularz Backus składni formularza (BNF)
W tym temacie przy użyciu składni BNF, który używa notacji pokazano w poniższej tabeli opisano skryptów używanych przez rejestrator ALT.  
  
|Konwencja/symbol|Znaczenie|  
|------------------------|-------------|  
|`::=`|Odpowiednik|  
|`&#124;`|LUB|  
|`X+`|Co najmniej jeden `X`s.|  
|`[X]`|`X`jest opcjonalna. Ograniczniki opcjonalne są wskazywane przez `[]`.|  
|Wszelkie **bold** tekstu|Literał ciągu.|  
|Wszelkie *kursywy* tekstu|Jak utworzyć literału ciągu.|  
  
 Jak wskazano w powyższej tabeli, skrypty rejestratora Używaj literałów ciągów. Te wartości są tekstu, który musi występować w skrypcie. W poniższej tabeli opisano Literały ciągu używany w skrypcie Rejestrator ALT.  
  
|Literał ciągu|Akcja|  
|--------------------|------------|  
|**ForceRemove**|Powoduje całkowite usunięcie następnego klucza (jeśli istnieje), a następnie ponownie tworzy go.|  
|**NoRemove**|Nie powoduje usunięcia klawisza Następna podczas Unregister.|  
|**Val**|Określa, że `<Key Name>` jest rzeczywiście nazwanej wartości.|  
|**Usuwanie**|Usuwa następny klucz w rejestrze.|  
|**s**|Określa, że wartość następnego ciąg (**REG_SZ**).|  
|**d**|Określa, że wartość następnego **DWORD** (**REG_DWORD**).|  
|**m**|Określa, że następna wartość ciągu wielokrotnego (**REG_MULTI_SZ**).|  
|**b**|Określa, że wartość następnego wartość binarną (**REG_BINARY**).|  
  
## <a name="bnf-syntax-examples"></a>Przykłady składni BNF  
 Oto kilka przykładów składni, aby lepiej zrozumieć, jak działają notacji i ciągów literałów w skrypcie Rejestrator ALT.  
  
### <a name="syntax-example-1"></a>Przykład składni 1  
  
```  
<registry expression> ::= <Add Key>  
```  
  
 Określa, że `registry expression` jest odpowiednikiem `Add Key`.  
  
### <a name="syntax-example-2"></a>Przykład składni 2  
  
```  
<registry expression> ::= <Add Key> | <Delete Key>  
```  
  
 Określa, że `registry expression` jest odpowiednikiem albo `Add Key` lub `Delete Key`.  
  
### <a name="syntax-example-3"></a>Przykład składni 3  
  
```  
<Key Name> ::= '<AlphaNumeric>+'  
```  
  
 Określa, że `Key Name` jest odpowiednikiem co najmniej jeden `AlphaNumerics`.  
  
### <a name="syntax-example-4"></a>Przykład składni 4  
  
```  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
```  
  
 Określa, że `Add Key` jest odpowiednikiem `Key Name`oraz że literałów ciągów `ForceRemove`, `NoRemove`, i `val`, są opcjonalne.  
  
### <a name="syntax-example-5"></a>Przykład składni 5  
  
```  
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0  
```  
  
 Określa, że `AlphaNumeric` jest równoważna do dowolny znak firmy innej niż NULL.  
  
### <a name="syntax-example-6"></a>Przykład składni 6  
  
```  
val 'testmulti' = m 'String 1\0String 2\0'  
```  
  
 Określa, że nazwa klucza `testmulti` wartość wielociągu składa się z `String 1` i `String 2`.  
  
### <a name="syntax-example-7"></a>Przykład składni 7  
  
```  
val 'testhex' = d '&H55'  
```  
  
 Określa, że nazwa klucza `testhex` jest **DWORD** wartość szesnastkową 55 (decimal 85). Ten format jest zgodna Uwaga **& H** notacji jako znaleziono w specyfikacji języka Visual Basic.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)

