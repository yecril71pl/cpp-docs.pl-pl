---
title: 'Kontenery kontrolek ActiveX: Ręczne Włączanie zawierania kontrolek ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f684bbb287213ad0cbe6d490c1bef869f5ffc9db
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077780"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Kontenery kontrolek ActiveX: ręczne włączanie zawierania kontrolek ActiveX

Jeśli nie została włączona obsługa formantu ActiveX, gdy Kreator aplikacji MFC jest używane do generowania aplikacji, należy ręcznie dodać tę obsługę. W tym artykule opisano proces ręcznego dodawania zawierania kontrolek ActiveX do istniejącej aplikacji kontenera OLE. Jeśli wcześniej wiadomo ma obsługi formantów ActiveX w kontenerze OLE, zobacz artykuł [Tworzenie kontenera kontrolek ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które wypierają ActiveX zobacz [formantów ActiveX](activex-controls.md).

> [!NOTE]
>  W tym artykule używany jest oparta na oknach dialogowych ActiveX kontroli kontenera projektu o nazwie kontener i osadzonego formantu o nazwie OK przykładowe w procedurach i kodu.

Aby zapewnić obsługę formantów ActiveX, należy dodać jeden wiersz kodu do dwóch plików projektu.

- Modyfikowanie w głównym oknie dialogowym `InitInstance` — funkcja (znajduje się w KONTENERZE. CPP) przez Kreatora aplikacji MFC, wywołuje element [afxenablecontrolcontainer —](reference/ole-initialization.md#afxenablecontrolcontainer), jak w poniższym przykładzie:

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Dodaj następujący kod do STDAFX projektu. Plik nagłówka H:

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Po wykonaniu tych czynności ponownie skompiluj projekt, klikając **kompilacji** na **kompilacji** menu.

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

