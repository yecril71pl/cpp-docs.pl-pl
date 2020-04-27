---
title: Przykłady skryptów rejestru
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 0e225ce28309aa619fd9436d8f4b93e60544e86c
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168751"
---
# <a name="registry-scripting-examples"></a>Przykłady skryptów rejestru

Przykłady skryptów w tym temacie przedstawiają sposób dodawania klucza do rejestru systemowego, rejestrowania serwera rejestratora COM i określania wielu drzew analizy.

## <a name="add-a-key-to-hkey_current_user"></a>Dodaj klucz do HKEY_CURRENT_USER

Poniższe drzewo analizy ilustruje prosty skrypt, który dodaje jeden klucz do rejestru systemowego. W szczególności skrypt dodaje klucz, `MyVeryOwnKey`, do. `HKEY_CURRENT_USER` Przypisuje również domyślną wartość ciągu `HowGoesIt` do nowego klucza:

```rgs
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Ten skrypt można łatwo rozszerzyć w celu zdefiniowania wielu podkluczy w następujący sposób:

```rgs
HKCU
{
    'MyVeryOwnKey' = s 'HowGoesIt'
    {
        'HasASubkey'
        {
            'PrettyCool' = d '55'
            val 'ANameValue' = s 'WithANamedValue'
        }
    }
}
```

Teraz skrypt dodaje podklucz, `HasASubkey`do. `MyVeryOwnKey` Do `PrettyCool` tego podklucza dodaje podklucz (z wartością domyślną `DWORD` 55) i `ANameValue` nazwaną wartość (z wartością ciągu `WithANamedValue`).

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>Rejestrowanie serwera rejestratora COM

Poniższy skrypt rejestruje samego serwera rejestratora COM.

```rgs
HKCR
{
    ATL.Registrar = s 'ATL Registrar Class'
    {
        CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'
    }
    NoRemove CLSID
    {
        ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = s 'ATL Registrar Class'
        {
            ProgID = s 'ATL.Registrar'
            InprocServer32 = s '%MODULE%'
            {
                val ThreadingModel = s 'Apartment'
            }
        }
    }
}
```

W czasie wykonywania to drzewo analizy dodaje `ATL.Registrar` klucz do. `HKEY_CLASSES_ROOT` Do tego nowego klucza:

- Określa `ATL Registrar Class` jako domyślną wartość ciągu klucza.

- Dodaje `CLSID` jako podklucz.

- Określa `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` dla `CLSID`elementu. (Ta wartość jest identyfikatorem CLSID rejestratora do użycia `CoCreateInstance`z.)

Ponieważ `CLSID` jest udostępniony, nie należy go usuwać w trybie wyrejestrowywania. Instrukcja, `NoRemove CLSID`, robi to, wskazując, że `CLSID` powinna być otwarta w trybie Register i ignorowana w trybie unregistering.

`ForceRemove` Instrukcja zawiera funkcję dla gospodarstw domowych, usuwając klucz i wszystkie jego podklucze przed ponownym utworzeniem klucza. Może to być przydatne, jeśli nazwy podkluczy zostały zmienione. W tym przykładzie skryptów program `ForceRemove` sprawdza, czy `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` już istnieje. Jeśli tak, `ForceRemove`:

- Usuwa `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` cyklicznie i wszystkie jego podklucze.

- Ponowne tworzenie `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Dodaje `ATL Registrar Class` jako domyślną wartość ciągu dla `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

Drzewo analizy dodaje teraz dwa nowe podklucze do `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. Pierwszy klawisz, `ProgID`, pobiera domyślną wartość ciągu, która jest ProgID. Drugi klucz, `InprocServer32`, pobiera domyślną wartość ciągu, `%MODULE%`, która jest wartością preprocesora wyjaśnioną w sekcji, [przy użyciu parametrów wymiennych (preprocesora rejestratora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)tego artykułu. `InprocServer32`Pobiera również nazwaną wartość `ThreadingModel`, z wartością ciągu. `Apartment`

## <a name="specify-multiple-parse-trees"></a>Określ wiele drzew analizy

Aby określić więcej niż jedno drzewo analizy w skrypcie, wystarczy umieścić jedno drzewo na końcu innego. Na przykład poniższy skrypt dodaje klucz, `MyVeryOwnKey`, do drzew analizy dla obu `HKEY_CLASSES_ROOT` i: `HKEY_CURRENT_USER`

```rgs
HKCR
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

> [!NOTE]
> W skrypcie rejestratora jest maksymalny rozmiar tokenu 4K. (Token jest dowolnym rozpoznawalnym elementem w składni). W `HKCR`poprzednim przykładzie `HKEY_CURRENT_USER` `'MyVeryOwnKey'`skryptu,,, i `'HowGoesIt'` są tokenami.

## <a name="see-also"></a>Zobacz także

[Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)
