---
title: Punkty wejścia wyeksportowanej funkcji DLL
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
ms.openlocfilehash: c521cad666864c728fd871b460cf0c92b815e414
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622642"
---
# <a name="exported-dll-function-entry-points"></a>Punkty wejścia wyeksportowanej funkcji DLL

W przypadku eksportowanych funkcji biblioteki DLL Użyj makra [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) , aby zachować właściwy stan globalny podczas przełączania z modułu DLL do biblioteki DLL aplikacji wywołującej.

Po wywołaniu to makro ustawia `pModuleState` , wskaźnik do `AFX_MODULE_STATE` struktury zawierającej dane globalne dla modułu, jako obowiązujący stan modułu dla pozostałej części zawierającego zakresu funkcji. Po opuszczeniu zakresu zawierającego makro zostanie automatycznie przywrócony poprzedni stan obowiązujących modułów.

To przełączanie jest osiągane przez konstruowanie instancji `AFX_MODULE_STATE` klasy na stosie. W konstruktorze Ta klasa uzyskuje wskaźnik do bieżącego stanu modułu i zapisuje je w zmiennej składowej, a następnie ustawia `pModuleState` jako nowy obowiązujący stan modułu. W jego destruktorze Ta klasa przywraca wskaźnik przechowywany w zmiennej składowej jako obowiązujący stan modułu.

Jeśli masz wyeksportowaną funkcję, taką jak ta, która uruchamia okno dialogowe w bibliotece DLL, musisz dodać następujący kod na początku funkcji:

[!code-cpp[NVC_MFCConnectionPoints#6](codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]

Spowoduje to zamianę bieżącego stanu modułu na stan zwrócony z [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) do końca bieżącego zakresu.

Problemy z zasobami w bibliotekach DLL będą wykonywane, jeśli `AFX_MANAGE_STATE` makro nie jest używane. Domyślnie MFC używa dojścia do zasobów głównej aplikacji do ładowania szablonu zasobu. Ten szablon jest w rzeczywistości przechowywany w bibliotece DLL. Główną przyczyną jest to, że informacje o stanie modułu MFC nie zostały przełączone przez `AFX_MANAGE_STATE` makro. Dojście do zasobu jest odzyskiwane z stanu modułu MFC. Nie przełączenie stanu modułu powoduje niewłaściwe użycie uchwytu zasobów.

`AFX_MANAGE_STATE`nie musi być umieszczony w każdej funkcji w bibliotece DLL. Na przykład, `InitInstance` może być wywoływana przez kod MFC w aplikacji bez względu na to, `AFX_MANAGE_STATE` że MFC automatycznie przesuwa stan modułu przed `InitInstance` , a następnie przełącza je ponownie po powrocie `InitInstance` . Ta sama wartość dotyczy wszystkich programów obsługi mapy komunikatów. Regularne biblioteki MFC DLL faktycznie mają specjalną procedurę okna głównego, która automatycznie przełącza stan modułu przed kierowaniem jakichkolwiek komunikatów.

## <a name="see-also"></a>Zobacz też

[Zarządzanie danymi stanu modułów MFC](managing-the-state-data-of-mfc-modules.md)
