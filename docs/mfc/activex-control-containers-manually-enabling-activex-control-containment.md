---
title: 'Kontenery formantów ActiveX: ręczne włączanie zawierania formantów ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: a8092a77020695163ce4fbacf7eeea2650ae9f86
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625115"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Kontenery formantów ActiveX: ręczne włączanie zawierania formantów ActiveX

Jeśli nie włączono obsługi kontrolki ActiveX podczas korzystania z Kreatora aplikacji MFC do wygenerowania aplikacji, musisz ręcznie dodać tę obsługę. W tym artykule opisano proces ręcznego dodawania kontrolki ActiveX do istniejącej aplikacji kontenera OLE. Jeśli wiesz, że w kontenerze OLE ma być obsługiwana Kontrolka ActiveX, zapoznaj się z artykułem [Tworzenie kontenera kontrolek ActiveX MFC](reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

> [!NOTE]
> W tym artykule jest stosowany oparty na oknach dialogowych projekt kontenera o nazwie Container i osadzony formant o nazwie okólnik jako przykłady w procedurach i kodzie.

Aby można było obsługiwać kontrolki ActiveX, należy dodać jeden wiersz kodu do dwóch plików projektu.

- Zmodyfikuj funkcję głównego okna dialogowego `InitInstance` (znajdującą się w kontenerze. CPP) przez Kreatora aplikacji MFC, wykonując wywołanie [AfxEnableControlContainer —](reference/ole-initialization.md#afxenablecontrolcontainer), tak jak w poniższym przykładzie:

   [!code-cpp[NVC_MFCOleContainer#34](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Dodaj następujące elementy do STDAFX projektu. Plik nagłówkowy H:

   [!code-cpp[NVC_MFCOleContainer#36](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Po wykonaniu tych kroków ponownie skompiluj projekt, klikając polecenie **Kompiluj** w menu **kompilacja** .

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](activex-control-containers.md)
