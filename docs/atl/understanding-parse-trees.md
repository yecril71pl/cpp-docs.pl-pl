---
title: Rejestrator ALT i drzewa analizy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb5b132e5e55ab5336254acaf4d2d3ae25440697
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-parse-trees"></a>Opis analizy drzew
Można zdefiniować co najmniej jeden drzewa analizy skryptu rejestratora, gdzie każdy drzewo analizy ma następujący format:  
  
```  
<root key>{<registry expression>}+  
```  
  
 gdzie:  
  
```  
<root key> ::= HKEY_CLASSES_ROOT | HKEY_CURRENT_USER |  
    HKEY_LOCAL_MACHINE | HKEY_USERS |  
    HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA |  
    HKEY_CURRENT_CONFIG | HKCR | HKCU |  
    HKLM | HKU | HKPD | HKDD | HKCC  
<registry expression> ::= <Add Key> | <Delete Key>  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
 [<Key Value>][{<Add Key>}]  
<Delete Key> ::= Delete<Key Name>  
<Key Name> ::= '<AlphaNumeric>+'  
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0  
<Key Value> ::== <Key Type><Key Name>  
<Key Type> ::= s | d  
<Key Value> ::= '<AlphaNumeric>'  
```  
  
> [!NOTE]
> `HKEY_CLASSES_ROOT` i `HKCR` są równoważne; `HKEY_CURRENT_USER` i `HKCU` są równoważne; i tak dalej.  
  
 Drzewo analizy można dodać wiele kluczy i podkluczy do \<klucz główny >. W ten sposób zapewnia dojścia podklucz Otwórz aż do zakończenia analizator analizowanie wszystkich jego podkluczy. Takie podejście jest bardziej efektywne niż korzysta z jednego klucza w czasie, jak pokazano w poniższym przykładzie:  
  
```  
HKEY_CLASSES_ROOT  
{  
 'MyVeryOwnKey'  
 {  
 'HasASubKey'  
 {  
 'PrettyCool'  
 }  
 }  
}  
```  
  
 W tym miejscu rejestratora początkowo otwiera (tworzy) `HKEY_CLASSES_ROOT\MyVeryOwnKey`. Widzi następnie który `MyVeryOwnKey` zawiera podklucz. Zamiast klawisz, aby zamknąć `MyVeryOwnKey`, rejestratora zachowuje dojście i otwiera (tworzy) `HasASubKey` przy użyciu tego uchwytu nadrzędnej. (Rejestru systemowego może być wolniejsze po otwarciu dojścia nadrzędnego). W związku z tym otwierania `HKEY_CLASSES_ROOT\MyVeryOwnKey` i otwierając `HasASubKey` z `MyVeryOwnKey` jako element nadrzędny jest szybsza niż otwierania `MyVeryOwnKey`zamykanie `MyVeryOwnKey`i otwierając `MyVeryOwnKey\HasASubKey`.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)

