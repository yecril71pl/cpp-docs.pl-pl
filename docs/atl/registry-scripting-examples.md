---
title: Przykłady skryptów rejestru
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 7bcdb7076982e2f0bd08f4fd82bb45f21e61ef20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329327"
---
# <a name="registry-scripting-examples"></a>Przykłady skryptów rejestru

Przykłady skryptów w tym temacie pokazują, jak dodać klucz do rejestru systemowego, zarejestrować serwer COM rejestratora i określić wiele drzew analizy.

## <a name="add-a-key-to-hkey_current_user"></a>Dodawanie klucza do HKEY_CURRENT_USER

Następujące drzewo analizy ilustruje prosty skrypt, który dodaje pojedynczy klucz do rejestru systemowego. W szczególności skrypt dodaje klucz, `MyVeryOwnKey` `HKEY_CURRENT_USER`do . Przypisuje również domyślną wartość `HowGoesIt` ciągu do nowego klucza:

```
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Ten skrypt można łatwo rozszerzyć, aby zdefiniować wiele podkluczów w następujący sposób:

```
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

Teraz skrypt dodaje `HasASubkey`podklucz, `MyVeryOwnKey`do . Do tego podklucza `PrettyCool` dodaje zarówno podklucz (z `DWORD` domyślną `ANameValue` wartością 55), `WithANamedValue`jak i nazwaną wartość (z wartością ciągu ).

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>Zarejestruj serwer COM rejestratora

Poniższy skrypt rejestruje sam serwer COM rejestratora.

```
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

W czasie wykonywania to drzewo analizy `ATL.Registrar` dodaje `HKEY_CLASSES_ROOT`klucz do . Do tego nowego klucza, to następnie:

- Określa `ATL Registrar Class` jako domyślną wartość ciągu klucza.

- Dodaje `CLSID` jako podklucz.

- Określa `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` dla `CLSID`. (Ta wartość jest CLSID rejestratora do użytku `CoCreateInstance`z .)

Ponieważ `CLSID` jest współużytkowana, nie należy go usuwać w trybie wyrejestrowania. Instrukcja `NoRemove CLSID`, robi to, `CLSID` wskazując, że powinny być otwierane w trybie rejestracji i ignorowane w trybie wyrejestrowania.

Instrukcja `ForceRemove` zapewnia funkcję sprzątania, usuwając klucz i wszystkie jego podkluczy przed ponownym utworzeniem klucza. Może to być przydatne, jeśli nazwy podkluczów uległy zmianie. W tym przykładzie `ForceRemove` skryptów `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` sprawdza, czy już istnieje. Jeśli tak, `ForceRemove`:

- Rekursywnie `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` usuwa i wszystkie jego podklucze.

- Odtwarzanie `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`pliku .

- Dodaje `ATL Registrar Class` jako domyślną `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`wartość ciągu dla .

Drzewo analizy dodaje teraz dwa nowe podklu skróty do `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. Pierwszy klucz `ProgID`, pobiera domyślną wartość ciągu, która jest ProgID. Drugi klucz, `InprocServer32`otrzymuje domyślną wartość `%MODULE%`ciągu, czyli wartość preprocesora wyjaśnioną w sekcji [Korzystanie z wymiennych parametrów (Preprocesor rejestratora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)tego artykułu. `InprocServer32`również pobiera nazwany `ThreadingModel`wartość, o wartości `Apartment`ciągu .

## <a name="specify-multiple-parse-trees"></a>Określanie wielu drzew analizy

Aby określić więcej niż jedno drzewo analizy w skrypcie, po prostu umieść jedno drzewo na końcu innego. Na przykład następujący skrypt dodaje `MyVeryOwnKey`klucz, do drzew analizy `HKEY_CLASSES_ROOT` dla `HKEY_CURRENT_USER`obu i:

```
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
> W skrypcie rejestratora 4K jest maksymalny rozmiar tokenu. (Token jest dowolnym rozpoznawalnym elementem w składni.) W poprzednim przykładzie `HKCR`skryptów `'MyVeryOwnKey'`, `'HowGoesIt'` , `HKEY_CURRENT_USER`i są wszystkie tokeny.

## <a name="see-also"></a>Zobacz też

[Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)
