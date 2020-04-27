---
title: Rejestratory i analizy ATL
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: de2cea9b0e7b7c62236f708f9aa8217eaa5df51d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168699"
---
# <a name="understanding-parse-trees"></a>Omówienie drzew analizy

Można zdefiniować co najmniej jeden drzewa analizy w skrypcie rejestratora, gdzie każde drzewo analizowane ma następującą postać:

> \<klucz główny> {\<wyrażenie rejestru>} +

gdzie:

> \<klucz główny>:: = HKEY_CLASSES_ROOT | HKEY_CURRENT_USER | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_LOCAL_MACHINE | HKEY_USERS | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_CURRENT_CONFIG | HKCR | HKCU | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKLM | HKU | HKPD | HKDD | HKCC

> \<wyrażenie rejestru>:: = \<dodaj klucz> | \<Usuń klucz>

> \<Dodaj klucz>:: = [**ForceRemove** | **NoRemove** | **Val**]\<nazwa klucza> [\<wartość klucza>] [{\<Add Key>}]

> \<Usuń klucz>:: = **Usuń**\<nazwę klucza>

> \<Nazwa klucza>:: = **"**\<alfanumeryczne>+**"**

> \<> alfanumeryczne:: = *dowolny znak, który nie ma wartości null, tj. ASCII 0*

> \<Wartość klucza>:: = \<typ klucza>\<nazwa klucza>

> \<Typ klucza>:: = **s** | **d**

> \<Wartość klucza>:: = **"**\<alfanumeryczne>**"**

> [!NOTE]
> `HKEY_CLASSES_ROOT`i `HKCR` są równoważne; `HKEY_CURRENT_USER` i `HKCU` są równoważne; i tak dalej.

Drzewo analizy może dodać wiele kluczy i podkluczy do klucza \<głównego>. W takim przypadku utrzymuje otwarte dojście podklucza do momentu zakończenia analizy wszystkich podkluczy przez analizator. Takie podejście jest bardziej wydajne niż obdziałanie jednego klucza w danym momencie, jak pokazano w poniższym przykładzie:

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

Tutaj zostanie otwarty Rejestrator (tworzony) `HKEY_CLASSES_ROOT\MyVeryOwnKey`. Następnie widzi, że `MyVeryOwnKey` ma podklucz. Zamiast zamknąć klucz do `MyVeryOwnKey`, rejestrator zachowuje uchwyt i otwiera (tworzy) `HasASubKey` przy użyciu tego dojścia nadrzędnego. (Rejestr systemu może być wolniejszy, gdy nie ma otwartego uchwytu nadrzędnego). W rezultacie otwieranie `HKEY_CLASSES_ROOT\MyVeryOwnKey` i otwieranie `HasASubKey` przy użyciu `MyVeryOwnKey` programu jako elementu nadrzędnego jest szybsze niż `MyVeryOwnKey`otwieranie, `MyVeryOwnKey`zamykanie i otwieranie `MyVeryOwnKey\HasASubKey`.

## <a name="see-also"></a>Zobacz także

[Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)
