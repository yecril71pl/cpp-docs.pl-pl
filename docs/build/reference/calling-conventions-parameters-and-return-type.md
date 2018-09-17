---
title: Konwencje wywoływania, parametry oraz zwracany typ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74aa2e58b7285ced1b49efc7f54c1ec11ad606c1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714756"
---
# <a name="calling-conventions-parameters-and-return-type"></a>Konwencje wywoływania, parametry oraz zwracany typ

Procedura pomocnika prototyp to:

```
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

### <a name="parameters"></a>Parametry

*pidd*<br/>
A `const` wskaźnik do `ImgDelayDescr` (patrz delayimp.h) zawierający przesunięcia różne dane dotyczące importowania, sygnaturę czasową, aby uzyskać informacje o powiązaniu i zestaw atrybutów, które zapewniają dodatkowe informacje o zawartości deskryptora. Obecnie ma tylko jeden atrybut `dlattrRva`, która wskazuje, że adresy w deskryptorze względnych adresów wirtualnych (w przeciwieństwie do wirtualnych adresów).

Dla definicji `PCImgDelayDescr` struktury, zobacz [struktura i stała — definicje](../../build/reference/structure-and-constant-definitions.md).

*ppfnIATEntry*<br/>
Wskaźnik do gniazda w opóźnionego ładowania Importuj tabelę adresu (IAT), należy zaktualizować przy użyciu adresu funkcji zaimportowane. Procedura pomocnika musi przechowywać tę samą wartość, która będzie zwracać do tej lokalizacji.

## <a name="expected-return-values"></a>Oczekiwano wartości zwracane

Jeśli funkcja się powiedzie, zwraca adresu funkcji zaimportowane.

Jeśli funkcja zawiedzie, zgłasza wyjątek i zwraca wartość 0. Może zostać wywołane trzy rodzaje wyjątków:

- Nieprawidłowy parametr, który się dzieje w przypadku atrybutów w `pidd` nie są poprawnie określone.

- `LoadLibrary` nie powiodło się na określonej biblioteki DLL.

- Niepowodzenie `GetProcAddress`.

Jest odpowiedzialny za obsługę tych wyjątków.

## <a name="remarks"></a>Uwagi

Konwencja wywoływania funkcji pomocnika to `__stdcall`. Typ zwracanej wartości nie jest istotne, więc FARPROC jest używany. Funkcja ta ma powiązanie C.

Wartość zwracana przez pomocnika obciążenia opóźnienia muszą być przechowywane w lokalizacji wskaźnika przekazany w funkcji, chyba że chcesz, aby Twoja procedura pomocnika ma być używany jako zaczepienia powiadomień. W takiej sytuacji kod jest odpowiedzialny za znalezienie wskaźnika odpowiednią funkcję do zwrócenia. Kod thunk, których konsolidator generuje następnie pobiera tę wartość zwracana jako rzeczywistych obiekt docelowy importu i przechodzi bezpośrednio do niego.

## <a name="sample"></a>Przykład

Poniższy kod przedstawia sposób implementowania funkcji podłączania proste.

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
PfnDliHook __pfnDliNotifyHook2 = delayHook;
*/
```

## <a name="see-also"></a>Zobacz też

[Ogólne informacje funkcji Pomocnik](../../build/reference/understanding-the-helper-function.md)