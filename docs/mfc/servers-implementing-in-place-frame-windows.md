---
title: 'Serwery: Implementowanie Windows ramowych w miejscu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24c63c10feff624abe399952b682303a6e262d35
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425018"
---
# <a name="servers-implementing-in-place-frame-windows"></a>Serwery: implementowanie okien ramowych w miejscu

W tym artykule opisano, co należy zrobić, aby zaimplementować okien ramowych w miejscu w visual edycji aplikacji serwera, jeśli nie używasz Kreatora aplikacji do tworzenia aplikacji serwera. Zamiast zgodnie z procedurą opisaną w tym artykule, można użyć istniejącej klasy okien ramowych w miejscu z aplikacji generowanych przez Kreatora aplikacji lub próbkę dostarczanych z programem Visual C++.

#### <a name="to-declare-an-in-place-frame-window-class"></a>Aby zadeklarować klasy okien ramowych w miejscu

1. Pochodzi z klasy okien ramowych w miejscu z `COleIPFrameWnd`.

   - W pliku nagłówka klasy, należy używać DECLARE_DYNCREATE — makro.

   - Użyj IMPLEMENT_DYNCREATE — makro w pliku implementacji (.cpp) klasy. Dzięki temu obiektów tej klasy, które ma zostać utworzony przez platformę.

1. Zadeklaruj `COleResizeBar` składowej w klasie okien ramowych. Jest to niezbędne, jeśli chcesz obsługiwać zmiany rozmiaru w miejscu aplikacji serwera.

     Zadeklaruj `OnCreate` obsługi wiadomości (przy użyciu **właściwości** okna) i wywoływać `Create` dla usługi `COleResizeBar` elementu członkowskiego, jeśli jego zdefiniowaniu.

1. Jeśli pasek narzędzi, Zadeklaruj `CToolBar` składowej w klasie okien ramowych.

     Zastąp `OnCreateControlBars` funkcję elementu członkowskiego, aby utworzyć pasek narzędzi, gdy serwer jest aktywny w miejscu. Na przykład:

     [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]

     Zawiera omówienie ten kod po kroku 5.

1. Uwzględnić plik nagłówka dla tej klasy okien ramowych w miejscu, w pliku głównym .cpp.

1. W `InitInstance` klasy aplikacji, można wywołać `SetServerInfo` funkcja obiektu szablonu dokumentu, aby określić zasoby i okno ramowe w miejscu, które ma być używany w otwartych i w miejscu do edycji.

Wywołuje szereg funkcji **Jeśli** instrukcja tworzy pasek narzędzi z zasobów z serwera, pod warunkiem. W tym momencie pasek narzędzi jest częścią hierarchii okno kontenera. Ponieważ ten pasek narzędzi jest tworzony na podstawie `CToolBar`, chyba że zmienił się właścicielem zostaną przetworzone jego wiadomości do jego właściciela aplikacji kontenera ramki okna. Dlatego wywołanie `SetOwner` jest konieczne. To wywołanie zmienia okna, w której polecenia są wysyłane do serwera w miejscu ramki okna co wiadomości, które mają być przekazane do serwera. Dzięki temu serwer reagować na operacje na pasku narzędzi, który zapewnia.

Identyfikator mapy bitowej narzędzi powinna być taka sama, jak inne zasoby w miejscu zdefiniowany w aplikacji serwera. Zobacz [menu i zasoby: dodatki do serwera](../mfc/menus-and-resources-server-additions.md) Aby uzyskać szczegółowe informacje.

Aby uzyskać więcej informacji, zobacz [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [COleResizeBar](../mfc/reference/coleresizebar-class.md), i [CDocTemplate::SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) w *odwołanie do biblioteki klas*.

## <a name="see-also"></a>Zobacz też

[Serwery](../mfc/servers.md)<br/>
[Serwery: implementowanie serwera](../mfc/servers-implementing-a-server.md)<br/>
[Serwery: implementowanie dokumentów serwera](../mfc/servers-implementing-server-documents.md)<br/>
[Serwery: elementy serwera](../mfc/servers-server-items.md)

