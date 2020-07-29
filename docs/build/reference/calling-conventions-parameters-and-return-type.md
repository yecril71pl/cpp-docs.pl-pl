---
title: Wywoływanie konwencji, parametrów oraz typu powrotu
ms.date: 02/13/2019
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
ms.openlocfilehash: 8813bab0cb55aa57792d0031433d96eefb095da4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223918"
---
# <a name="calling-conventions-parameters-and-return-type"></a>Wywoływanie konwencji, parametrów oraz typu powrotu

Prototyp procedury pomocnika:

```
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

### <a name="parameters"></a>Parametry

*pidd*<br/>
**`const`** Wskaźnik do obiektu `ImgDelayDescr` , który zawiera przesunięcia różnych danych związanych z importem, sygnaturę czasową do powiązania informacji oraz zestaw atrybutów, które zawierają dodatkowe informacje o zawartości deskryptora. Obecnie istnieje tylko jeden atrybut, `dlattrRva` który wskazuje, że adresy w deskryptorze są względnymi adresami wirtualnymi. Aby uzyskać więcej informacji, zobacz Deklaracje w *delayimp. h*.

Aby zapoznać się z definicją `PCImgDelayDescr` struktury, zobacz [Struktura i definicje stałe](structure-and-constant-definitions.md).

*ppfnIATEntry*<br/>
Wskaźnik do gniazda w tabeli adresów importu opóźnionego ładowania (IAT), który jest aktualizowany przy użyciu adresu zaimportowanej funkcji. Procedura pomocnika musi przechowywać tę samą wartość, która zwraca do tej lokalizacji.

## <a name="expected-return-values"></a>Oczekiwane wartości zwracane

Jeśli funkcja się powiedzie, zwraca adres zaimportowanej funkcji.

Jeśli funkcja się nie powiedzie, zgłasza wyjątek i zwraca 0. Można podwyższyć trzy typy wyjątków:

- Nieprawidłowy parametr, co się stanie, jeśli atrybuty w `pidd` nie zostały określone poprawnie.

- `LoadLibrary`Niepowodzenie dla określonej biblioteki DLL.

- Niepowodzenie `GetProcAddress` .

Jest odpowiedzialny za obsługę tych wyjątków.

## <a name="remarks"></a>Uwagi

Konwencja wywoływania dla funkcji pomocnika to **`__stdcall`** . Typ wartości zwracanej nie jest odpowiedni, więc FARPROC jest używany. Ta funkcja ma powiązanie C.

Wartość zwracana pomocnika ładowania opóźnienia musi być przechowywana w lokalizacji wskaźnika funkcji przekazanej, chyba że chcesz, aby procedura pomocnika była używana jako punkt zaczepienia powiadomienia. W takim przypadku kod jest odpowiedzialny za znalezienie odpowiedniego wskaźnika funkcji do zwrócenia. Kod thunk, który generuje, następnie pobiera wartość zwracaną jako rzeczywisty element docelowy importu i przechodzi bezpośrednio do niego.

## <a name="sample"></a>Przykład

Poniższy kod pokazuje, jak zaimplementować prostą funkcję haka.

```C
FARPROC WINAPI delayHook(unsigned dliNotify, PDelayLoadInfo pdli)
{
    switch (dliNotify) {
        case dliStartProcessing :

            // If you want to return control to the helper, return 0.
            // Otherwise, return a pointer to a FARPROC helper function
            // that will be used instead, thereby bypassing the rest
            // of the helper.

            break;

        case dliNotePreLoadLibrary :

            // If you want to return control to the helper, return 0.
            // Otherwise, return your own HMODULE to be used by the
            // helper instead of having it call LoadLibrary itself.

            break;

        case dliNotePreGetProcAddress :

            // If you want to return control to the helper, return 0.
            // If you choose you may supply your own FARPROC function
            // address and bypass the helper's call to GetProcAddress.

            break;

        case dliFailLoadLib :

            // LoadLibrary failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_MOD_NOT_FOUND) and exit.
            // If you want to handle the failure by loading an alternate
            // DLL (for example), then return the HMODULE for
            // the alternate DLL. The helper will continue execution with
            // this alternate DLL and attempt to find the
            // requested entrypoint via GetProcAddress.

            break;

        case dliFailGetProc :

            // GetProcAddress failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_PROC_NOT_FOUND) and exit.
            // If you choose you may handle the failure by returning
            // an alternate FARPROC function address.

            break;

        case dliNoteEndProcessing :

            // This notification is called after all processing is done.
            // There is no opportunity for modifying the helper's behavior
            // at this point except by longjmp()/throw()/RaiseException.
            // No return value is processed.

            break;

        default :

            return NULL;
    }

    return NULL;
}

/*
and then at global scope somewhere
const PfnDliHook __pfnDliNotifyHook2 = delayHook;
*/
```

## <a name="see-also"></a>Zobacz także

[Zrozumienie funkcji pomocnika](understanding-the-helper-function.md)
