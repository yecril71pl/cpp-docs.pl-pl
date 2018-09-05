---
title: Rejestrator ALT i drzew analizy | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 561bfa3e307a08c6a3560a6a8b6d3bebd8598343
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751198"
---
# <a name="understanding-parse-trees"></a>Opis drzew analizy

Można zdefiniować co najmniej jeden drzew analizy skryptu rejestratora, gdzie każdy drzewo analizy ma następującą postać:

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
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name> [<Key Value>][{<Add Key>}]  
<Delete Key> ::= Delete<Key Name>  
<Key Name> ::= '<AlphaNumeric>+'  
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0  
<Key Value> ::== <Key Type><Key Name>  
<Key Type> ::= s | d  
<Key Value> ::= '<AlphaNumeric>'  
```

> [!NOTE]
> `HKEY_CLASSES_ROOT` i `HKCR` są równoważne; `HKEY_CURRENT_USER` i `HKCU` są równoważne; i tak dalej.

Drzewo analizy można dodać wiele kluczy i podkluczy do \<klucz główny >. W ten sposób zapewnia podklucz dojście otwartego dopóki nie zakończy się analizator składni podczas analizowania wszystkich jego podkluczy. To podejście jest bardziej wydajne niż wykonywanie operacji na jeden klucz w czasie, jak pokazano w poniższym przykładzie:

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

W tym miejscu Rejestrator początkowo otwiera (tworzy) `HKEY_CLASSES_ROOT\MyVeryOwnKey`. Go następnie przygląda się, że `MyVeryOwnKey` ma podklucza. Zamiast klawisz, aby zamknąć `MyVeryOwnKey`, Rejestrator przechowuje dojście i otwiera (tworzy) `HasASubKey` przy użyciu tego uchwytu nadrzędnej. (Rejestru systemowego może być wolniejsze gdy brak dojścia nadrzędny jest otwarty). W związku z tym, otwierając `HKEY_CLASSES_ROOT\MyVeryOwnKey` , a następnie otwarcie `HasASubKey` z `MyVeryOwnKey` jako element nadrzędny jest szybsza niż otwierania `MyVeryOwnKey`, zamykanie `MyVeryOwnKey`i otwierając `MyVeryOwnKey\HasASubKey`.

## <a name="see-also"></a>Zobacz też

[Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)

