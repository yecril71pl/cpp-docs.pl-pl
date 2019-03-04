---
title: Przykłady skryptów rejestru
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: dffdd111d33d6fbd845e1534cdef1d5c8e1749d2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262938"
---
# <a name="registry-scripting-examples"></a>Przykłady skryptów rejestru

Przykłady skryptów, w tym temacie pokazują, jak dodać klucz do rejestru systemowego, Zarejestruj serwer COM rejestratora i określ wiele drzew analizy.

## <a name="add-a-key-to-hkeycurrentuser"></a>Dodaje klucz do HKEY_CURRENT_USER

W poniższym drzewie analizy przedstawiono prosty skrypt, który dodaje jeden klucz w rejestrze systemu. W szczególności skrypt ten dodaje klucz, `MyVeryOwnKey`, `HKEY_CURRENT_USER`. Przypisuje także domyślną wartość ciągu `HowGoesIt` do nowego klucza:

```
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Ten skrypt można łatwo rozszerzyć w taki sposób, aby zdefiniować wiele podkluczy w następujący sposób:

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

Teraz, skrypt ten dodaje podklucz `HasASubkey`, `MyVeryOwnKey`. Do tego podklucza dodaje ona zarówno `PrettyCool` podklucz (domyślnie `DWORD` wartość 55) i `ANameValue` nazwanej wartości (przy użyciu wartości ciągu `WithANamedValue`).

##  <a name="_atl_register_the_registrar_com_server"></a> Zarejestruj serwer COM rejestratora

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

W czasie wykonywania, dodaje ten drzewo analizy `ATL.Registrar` klucza `HKEY_CLASSES_ROOT`. Do tego nowego klucza następnie it:

- Określa `ATL Registrar Class` jako klucz-wartość domyślną w ciągu.

- Dodaje `CLSID` jako podklucz.

- Określa `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` dla `CLSID`. (Ta wartość jest rejestratora CLSID, do użytku z programem `CoCreateInstance`.)

Ponieważ `CLSID` jest udostępniony, go nie należy usuwać w trybie Unregister. Instrukcja `NoRemove CLSID`, wykonuje to zadanie, co oznacza, że `CLSID` powinien być otwarty w trybie rejestrze i w trybie Wyrejestruj ignorowane.

`ForceRemove` Instrukcja oferuje funkcję celów przez usunięcie klucza i wszystkich jego podkluczy przed następuje ponowne tworzenie klucza. Może to być przydatne, jeśli zmieniły się nazwami podkluczy. W tym przykładzie skryptów `ForceRemove` sprawdza, czy `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` już istnieje. Jeśli tak jest, `ForceRemove`:

- Rekursywnie usuwa `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` i wszystkich jego podkluczy.

- Ponownie tworzy `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Dodaje `ATL Registrar Class` jako domyślną wartość ciągu dla `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

W drzewie analizy dodano dwa nowe podklucze do `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. Pierwszy klucz `ProgID`, pobiera wartość domyślną ciągu, który jest identyfikator ProgID. Drugi klucz `InprocServer32`, pobiera wartość domyślną ciągu `%MODULE%`, która jest wartością preprocesora opisane w sekcji [przy użyciu zastępowalnych parametrów (Preprocesor rejestratora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md), części tego artykułu. `InprocServer32` zapewnia również nazwanej wartości `ThreadingModel`, z wartością ciągu `Apartment`.

## <a name="specify-multiple-parse-trees"></a>Określ wiele drzew analizy

Aby określić więcej niż jeden drzewo analizy w skrypcie, po prostu umieść jednym drzewie pod koniec drugiego. Na przykład, poniższy skrypt dodaje klucz, `MyVeryOwnKey`, aby drzew analizy dla obu `HKEY_CLASSES_ROOT` i `HKEY_CURRENT_USER`:

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
> W przypadku skryptu rejestratora 4K jest maksymalny rozmiar tokenu. (Token jest dowolny element rozpoznawalną w składni). W poprzednim przykładzie skryptów `HKCR`, `HKEY_CURRENT_USER`, `'MyVeryOwnKey'`, i `'HowGoesIt'` są wszystkie tokeny.

## <a name="see-also"></a>Zobacz także

[Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)
