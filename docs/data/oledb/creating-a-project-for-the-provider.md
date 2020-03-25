---
title: Tworzenie projektu dla dostawcy
ms.date: 10/22/2018
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
ms.openlocfilehash: f2ff42ba8a2e908f672db7e96fc9f24f51a1fd9b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211409"
---
# <a name="creating-a-project-for-the-provider"></a>Tworzenie projektu dla dostawcy

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>Aby utworzyć projekt, w którym będzie znajdować się dostawca OLE DB

1. W menu **File** (Plik) kliknij pozycję **New** (Nowe), a następnie kliknij pozycję **Project** (Projekt).

   Zostanie wyświetlone okno dialogowe **Nowy projekt**.

1. W okienku **typy projektów** kliknij ikonę **zainstalowane** > **Visual C++**  > **MFC/ATL** . W okienku **Szablony** kliknij pozycję **Projekt ATL**.

    > [!NOTE]
    > W poprzednich wersjach programu Visual Studio Znajdź typ projektu w obszarze **zainstalowane** > **Szablony** > **Visual C++**  > **ATL**.

1. W polu **Nazwa** wprowadź nazwę projektu, a następnie kliknij przycisk **OK**.

   Zostanie wyświetlony **Kreator projektu ATL** .

1. W **Kreatorze projektu ATL**wybierz **bibliotekę dołączaną dynamicznie (dll)** dla **typu aplikacji**.

1. Kliknij przycisk **Finish** (Zakończ).

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
