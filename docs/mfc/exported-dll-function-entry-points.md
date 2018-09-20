---
title: Wyeksportowane punkty wejścia funkcji DLL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b6bc9d6664ef1846523d5da90553e4a9e8cc6c4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444121"
---
# <a name="exported-dll-function-entry-points"></a>Punkty wejścia wyeksportowanej funkcji DLL

Do eksportowanych funkcji biblioteki dll, należy użyć [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) makra w celu prawidłowego stanu globalnego podczas przełączania z modułu DLL do biblioteki DLL z aplikacji wywołującej.

Gdy zostanie wywołana, to makro ustawia `pModuleState`, wskaźnik do `AFX_MODULE_STATE` struktury zawierającej dane globalne dla modułu, jako stan modułu efektywne na pozostałą zawierającego zakresu funkcji. Po opuszczeniu zakres zawierający makra, zostanie automatycznie przywrócony poprzedniego stanu modułu skuteczne.

To przełączanie odbywa się przez utworzenie wystąpienia `AFX_MODULE_STATE` klasy na stosie. W jego konstruktorze tej klasy uzyskuje wskaźnik do bieżącego stanu modułu i zapisuje ją w zmiennej składowej, a następnie ustawia `pModuleState` jako nowy stan modułu skuteczne. W destruktorze ta klasa przywraca wskaźnika, przechowywane w jego zmiennej składowej jako stanu modułu skuteczne.

Jeśli masz eksportowanych funkcji, takich jak taki, który uruchamia okno dialogowe w bibliotece DLL, musisz Dodaj następujący kod na początku funkcji:

[!code-cpp[NVC_MFCConnectionPoints#6](../mfc/codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]

Zamienia to bieżący stan modułu ze stanem zwróciło [AfxGetStaticModuleState —](reference/extension-dll-macros.md#afxgetstaticmodulestate) aż do końca bieżącego zakresu.

Problemy z zasobami w bibliotekach DLL wystąpi `AFX_MANAGE_STATE` makr nie jest używany. Domyślnie MFC wykorzystuje uchwyt zasobów aplikacji głównej można załadować szablonu zasobów. Ten szablon rzeczywiście jest przechowywana w bibliotece DLL. Główną przyczyną jest informacje o stanie modułu MFC nie został przełączony przez `AFX_MANAGE_STATE` makra. Dojście do zasobu jest odzyskiwany od stanu modułu MFC. Nie przełączenie stanu modułu powoduje, że dojście niewłaściwych zasobów ma być używany.

`AFX_MANAGE_STATE` nie musi znajdować się w każdej funkcji w bibliotece DLL. Na przykład `InitInstance` może być wywoływany przez kod MFC w aplikacji bez `AFX_MANAGE_STATE` ponieważ MFC jest kierowany w stanie modułu przed `InitInstance` i następnie przełączników je z powrotem po `InitInstance` zwraca. To samo dotyczy obsługi mapie komunikatów. Regularne biblioteki DLL MFC faktycznie istnieje procedura specjalne okna głównego, która automatycznie przełącza moduł przed przesłaniem wszystkie komunikaty.

## <a name="see-also"></a>Zobacz też

[Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

