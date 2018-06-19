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
ms.openlocfilehash: 1be4c74a48f1367369582b433a2a833ceb8e1976
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343856"
---
# <a name="exported-dll-function-entry-points"></a>Punkty wejścia wyeksportowanej funkcji DLL
Dla eksportowanych funkcji biblioteki dll, użyj [afx_manage_state —](reference/extension-dll-macros.md#afx_manage_state) makra w celu prawidłowego stanu globalnego podczas przełączania z modułu DLL do biblioteki DLL z aplikacji wywołującej.  
  
 Po tym makro ustawia `pModuleState`, wskaźnik do `AFX_MODULE_STATE` struktury zawierającej dane globalne dla modułu, jak stan modułu skuteczne dla pozostałych zawierający zakres funkcji. Opuszczających zakres zawierający makro poprzedniego stanu modułu skuteczne zostanie automatycznie przywrócony.  
  
 To przełączanie jest to osiągane przez utworzenie wystąpienia **afx_module_state —** klasy na stosie. W jego konstruktorze tej klasy uzyskuje wskaźnik do bieżący stan modułu i zapisuje je w zmiennej członkowskiej, a następnie ustawia `pModuleState` jako nowy stan modułu skuteczne. W jego destruktora tej klasy przywraca wskaźnika przechowywane w jego zmiennej członkowskiej jako stan modułu skuteczne.  
  
 Jeśli masz wyeksportowanej funkcji, takiej jak uruchamia okno dialogowe w bibliotece DLL należy dodać następujący kod na początku funkcji:  
  
 [!code-cpp[NVC_MFCConnectionPoints#6](../mfc/codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]  
  
 Zamienia to bieżący stan modułu ze stanem zwrócony z [AfxGetStaticModuleState —](reference/extension-dll-macros.md#afxgetstaticmodulestate) do końca bieżącego zakresu.  
  
 Problemy z zasobami w bibliotekach DLL wystąpi, jeśli `AFX_MANAGE_STATE` makro nie jest używany. Domyślnie MFC używa zasobów dojście aplikacji głównej do załadowania szablonu zasobów. Ten szablon faktycznie jest przechowywany w bibliotece DLL. Główną przyczyną jest informacji o stanie modułu MFC nie został przełączony przez `AFX_MANAGE_STATE` makra. Dojście do zasobu jest odzyskiwana ze stanu modułu MFC. Nie przełączający stan modułu powoduje, że dojście niewłaściwego zasobu do użycia.  
  
 `AFX_MANAGE_STATE` nie musi znajdować się w każdej funkcji w bibliotece DLL. Na przykład `InitInstance` może być wywoływany przez kod MFC w aplikacji bez `AFX_MANAGE_STATE` ponieważ MFC automatycznie przenosi stan modułu przed `InitInstance` , a następnie przełącza ją tu później za `InitInstance` zwraca. Dotyczy to wszystkich programów obsługi wiadomości mapy. Regularne biblioteki DLL MFC faktycznie mają specjalne okna głównego procedury, która automatycznie zmienia stan modułu przed przesłaniem wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

