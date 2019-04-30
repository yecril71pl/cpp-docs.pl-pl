---
title: 'Kontenery kontrolek ActiveX: Ręczne włączanie zawierania kontrolek ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 80ca25192f3dbda711b0398917cfa68571cd2c55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394939"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Kontenery kontrolek ActiveX: Ręczne włączanie zawierania kontrolek ActiveX

Jeśli nie została włączona obsługa formantu ActiveX, gdy Kreator aplikacji MFC jest używane do generowania aplikacji, należy ręcznie dodać tę obsługę. W tym artykule opisano proces ręcznego dodawania zawierania kontrolek ActiveX do istniejącej aplikacji kontenera OLE. Jeśli wcześniej wiadomo ma obsługi formantów ActiveX w kontenerze OLE, zobacz artykuł [Tworzenie kontenera kontrolek ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](activex-controls.md).

> [!NOTE]
>  W tym artykule używany jest oparta na oknach dialogowych ActiveX kontroli kontenera projektu o nazwie kontener i osadzonego formantu o nazwie OK przykładowe w procedurach i kodu.

Aby zapewnić obsługę formantów ActiveX, należy dodać jeden wiersz kodu do dwóch plików projektu.

- Modyfikowanie w głównym oknie dialogowym `InitInstance` — funkcja (znajduje się w KONTENERZE. CPP) przez Kreatora aplikacji MFC, wywołuje element [afxenablecontrolcontainer —](reference/ole-initialization.md#afxenablecontrolcontainer), jak w poniższym przykładzie:

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Dodaj następujący kod do STDAFX projektu. Plik nagłówka H:

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Po wykonaniu tych czynności ponownie skompiluj projekt, klikając **kompilacji** na **kompilacji** menu.

## <a name="see-also"></a>Zobacz także

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)
