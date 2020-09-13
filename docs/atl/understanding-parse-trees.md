---
title: Rejestratory i analizy ATL
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: ff74ff879e757a569232ff19244d3f7598063465
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040291"
---
# <a name="understanding-parse-trees"></a>Omówienie drzew analizy

Można zdefiniować co najmniej jeden drzewa analizy w skrypcie rejestratora, gdzie każde drzewo analizowane ma następującą postać:

> \<root key>{\<registry expression>}+

gdzie:

> \<root key> :: = HKEY_CLASSES_ROOT \| HKEY_CURRENT_USER \|\
> &emsp;HKEY_LOCAL_MACHINE \| HKEY_USERS \|\
> &emsp;HKEY_PERFORMANCE_DATA \| HKEY_DYN_DATA \|\
> &emsp;HKEY_CURRENT_CONFIG \| HKCR \| HKCU \|\
> &emsp;HKLM \| HKU \| HKPD \| HKDD \| HKCC

> \<registry expression>::= \<Add Key> \|\<Delete Key>

> \<Add Key>:: = \[ **ForceRemove** \| **NoRemove** \| **Val**] \<Key Name> [ \<Key Value> ] [{ \<Add Key> }]

> \<Delete Key> :: = **Delete**\<Key Name>

> \<Key Name> ::= **'**\<AlphaNumeric>+**'**

> \<AlphaNumeric> :: = *dowolny znak, który nie ma wartości null, tj. ASCII 0*

> \<Key Value> ::= \<Key Type>\<Key Name>

> \<Key Type> :: = **s** \| **d**

> \<Key Value> ::= **'**\<AlphaNumeric>**'**

> [!NOTE]
> `HKEY_CLASSES_ROOT` i `HKCR` są równoważne; `HKEY_CURRENT_USER` i `HKCU` tak dalej.

Drzewo analizy może dodać wiele kluczy i podkluczy do \<root key> . W takim przypadku utrzymuje otwarte dojście podklucza do momentu zakończenia analizy wszystkich podkluczy przez analizator. Takie podejście jest bardziej wydajne niż obdziałanie jednego klucza w danym momencie, jak pokazano w poniższym przykładzie:

```rgs
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

Tutaj zostanie otwarty Rejestrator (tworzony) `HKEY_CLASSES_ROOT\MyVeryOwnKey` . Następnie widzi, że `MyVeryOwnKey` ma podklucz. Zamiast zamknąć klucz do `MyVeryOwnKey` , rejestrator zachowuje uchwyt i otwiera (tworzy) `HasASubKey` przy użyciu tego dojścia nadrzędnego. (Rejestr systemu może być wolniejszy, gdy nie ma otwartego uchwytu nadrzędnego). W rezultacie otwieranie `HKEY_CLASSES_ROOT\MyVeryOwnKey` i otwieranie `HasASubKey` przy użyciu `MyVeryOwnKey` programu jako elementu nadrzędnego jest szybsze niż otwieranie `MyVeryOwnKey` , zamykanie `MyVeryOwnKey` i otwieranie `MyVeryOwnKey\HasASubKey` .

## <a name="see-also"></a>Zobacz także

[Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)
