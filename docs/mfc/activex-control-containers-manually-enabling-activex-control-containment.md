---
title: 'Kontenery formantów ActiveX: ręczne włączanie zawierania formantów ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 94ad6e8356b5dab54ae97dbdd90812039d1425c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322066"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Kontenery formantów ActiveX: ręczne włączanie zawierania formantów ActiveX

Jeśli obsługa kontroli ActiveX nie została włączona podczas generowania aplikacji przez Kreatora aplikacji MFC, należy dodać tę obsługę ręcznie. W tym artykule opisano proces ręcznego dodawania zamknięcia formantu ActiveX do istniejącej aplikacji kontenera OLE. Jeśli z góry wiesz, że chcesz obsługiwać kontrolę ActiveX w kontenerze OLE, zobacz artykuł [Tworzenie kontenera sterowania MFC ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

> [!NOTE]
> W tym artykule użyto opartego na oknie dialogowym projektu kontenera formantu ActiveX o nazwie Kontener i osadzonego formantu o nazwie Circ jako przykłady w procedurach i kodzie.

Aby obsługiwać formanty ActiveX, należy dodać jeden wiersz kodu do dwóch plików projektu.

- Zmodyfikuj `InitInstance` funkcję głównego okna dialogowego (można znaleźć w kontenerze. CPP) przez Kreatora aplikacji MFC, który dzwoni do [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer), jak w poniższym przykładzie:

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Dodaj następujące elementy do programu STDAFX projektu. H plik nagłówka:

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Po wykonaniu tych kroków odbuduj projekt, klikając polecenie **Buduj** w menu **Kompilacja.**

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)
