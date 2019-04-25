---
title: Rejestrator ALT i drzew analizy
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: e1aea573e78e6f6a9a86bc4e3987ee448815f329
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196171"
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

## <a name="see-also"></a>Zobacz także

[Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)
