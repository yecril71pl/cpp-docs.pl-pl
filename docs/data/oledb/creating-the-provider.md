---
title: Tworzenie dostawcy
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 7a8b4caf85ff7d0310c97cb953739796cca21c43
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707577"
---
# <a name="creating-the-provider"></a>Tworzenie dostawcy

::: moniker range="vs-2019"

Kreator ATL OLE DB Provider nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Aby utworzyć dostawcę OLE DB przy użyciu biblioteki ATL OLE DB Provider Kreatora

1. Kliknij prawym przyciskiem myszy projekt.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

1. W **Dodaj klasę** dialogowego **zainstalowane** > **Visual C++**  > **ATL**, wybierz opcję **Dostawcy OLE DB ATL** ikonę, a następnie kliknij przycisk **Otwórz**.

1. W **Kreator biblioteki ATL OLE DB Provider**, podaj krótką nazwę dostawcy w **krótką nazwę** pole. Poniższe tematy Użyj krótkiej nazwy *niestandardowe*, ale można użyć innej nazwy. Pozostałe pola nazw wypełnić według nazwy, które można wprowadzić.

1. Edytuj pozostałe pola nazw, jeśli to konieczne. Oprócz obiektowe i plikowe nazwy można edytować następujących czynności:

   - **Klasa coclass**: Nazwa która używa modelu COM w celu utworzenia dostawcy.

   - **Identyfikator progID**: Identyfikator programowy, czyli ciąg tekstowy, który można używać zamiast identyfikatora GUID.

   - **Wersja**: Używane z ProgID i Coclass, aby wygenerować identyfikator programowy zależne od wersji

1. Kliknij przycisk **Zakończ**.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
