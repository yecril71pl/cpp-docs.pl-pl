---
title: Tworzenie projektu dla dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0f4049190ac30cfff634d4cfef82410ccfdf1314
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063084"
---
# <a name="creating-a-project-for-the-provider"></a>Tworzenie projektu dla dostawcy

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>Aby utworzyć projekt, w której będą znajdować się w dostawcy OLE DB

1. Z **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.

   **Nowy projekt** pojawi się okno dialogowe.

1. W **typów projektów** okienku kliknij **zainstalowane** > **Visual C++** > **MFC i ATL** folderu. W **szablony** okienku kliknij **Projekt ATL**.

    > [!NOTE]
    > W poprzednich wersjach programu Visual Studio, Znajdź typ projektu w obszarze **zainstalowane** > **szablony** > **Visual C++**  >  **ATL**.

1. W **nazwa** , wprowadź nazwę dla projektu, a następnie kliknij **OK**.

   **Kreator projektów ATL** pojawia się.

1. W **Kreator projektów ATL**, wybierz **Biblioteka dołączana dynamicznie (DLL)** dla **typ aplikacji**.

1. Kliknij przycisk **Zakończ**.

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)