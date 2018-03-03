---
title: "Konwencje wywoływania, parametry oraz zwracany typ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3c57a1a4fe659819d8635b2a6a05d565ffa95250
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="calling-conventions-parameters-and-return-type"></a>Konwencje wywoływania, parametry oraz zwracany typ
Prototyp procedury pomocnika jest:  
  
```  
FARPROC WINAPI __delayLoadHelper2(   
   PCImgDelayDescr pidd,  
   FARPROC * ppfnIATEntry  
);  
```  
  
 gdzie:  
  
 `pidd`  
 A `const` wskaźnik do `ImgDelayDescr` (zobacz delayimp.h) zawierający przesunięcia różne dane dotyczące importowania, timestamp, aby uzyskać informacje o powiązaniu i zestaw atrybutów, które zapewniają dodatkowe informacje o zawartości deskryptora. Obecnie istnieje tylko jeden atrybut `dlattrRva`, który wskazuje, że adresy w deskryptorze względną wirtualnych adresów (w przeciwieństwie do adresów wirtualnych).  
  
 Definicja `PCImgDelayDescr` struktury, zobacz [struktura i stała — definicje](../../build/reference/structure-and-constant-definitions.md).  
  
 `ppfnIATEntry`  
 Wskaźnik do miejsca w opóźnionego ładowania Importuj tabelę adresu (IAT) aktualizacji przy użyciu adresu funkcji zaimportowany. Procedura pomocnika musi przechowywać taką samą wartość, która będzie zwracać w tej lokalizacji.  
  
## <a name="expected-return-values"></a>Oczekiwano wartości zwracane  
 Jeśli funkcja zakończy się pomyślnie, zwraca adresu funkcji zaimportowany.  
  
 W przypadku niepowodzenia funkcji zgłasza wyjątek i zwraca wartość 0. Może zostać wywołane trzy typy wyjątków:  
  
-   Nieprawidłowy parametr, który się stanie w przypadku atrybutów w `pidd` nie są określone poprawnie.  
  
-   `LoadLibrary`nie powiodło się w określonym pliku DLL.  
  
-   Niepowodzenie `GetProcAddress`.  
  
 Jest Twoje odpowiedzialność za obsługę tych wyjątków.  
  
## <a name="remarks"></a>Uwagi  
 Konwencja wywoływania funkcji pomocnika jest `__stdcall`. Typ wartości zwracanej nie jest istotne, więc FARPROC jest używany. Ta funkcja ma powiązanie C.  
  
 Zwracana wartość pomocnika obciążenia opóźnienie musi być przechowywany w lokalizacji wskaźnik przekazany w funkcji, chyba że chcesz z procedury pomocnika ma być używany jako haku powiadomień. W takim przypadku kodu jest odpowiedzialny za znajdowanie wskaźnika odpowiednią funkcję do zwrócenia. Kod thunk konsolidator generuje następnie pobiera tej wartości zwracanej docelowo rzeczywistego importu i przechodzi do niego bezpośrednio.  
  
## <a name="sample"></a>Przykład  
 Poniższy kod przedstawia sposób implementacji funkcji haku proste.  
  
```  
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