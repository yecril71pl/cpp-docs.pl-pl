---
title: Tworzenie dostawcy
ms.date: 10/15/2018
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 6258b5247e4d9d027e0f03bc133dff1a059665bd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032353"
---
# <a name="creating-the-provider"></a>Tworzenie dostawcy

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Aby utworzyć dostawcę OLE DB przy użyciu biblioteki ATL OLE DB Provider Kreatora

1. Kliknij prawym przyciskiem myszy projekt.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

1. W **Dodaj klasę** dialogowego **zainstalowane** > **Visual C++** > **ATL**, wybierz **Dostawcy OLE DB ATL** ikonę, a następnie kliknij przycisk **Otwórz**.

1. W **Kreator biblioteki ATL OLE DB Provider**, podaj krótką nazwę dostawcy w **krótką nazwę** pole. Poniższe tematy Użyj krótkiej nazwy *niestandardowe*, ale można użyć innej nazwy. Pozostałe pola nazw wypełnić według nazwy, które można wprowadzić.

1. Edytuj pozostałe pola nazw, jeśli to konieczne. Oprócz obiektowe i plikowe nazwy można edytować następujących czynności:

   - **Klasa coclass**: Nazwa która używa modelu COM w celu utworzenia dostawcy.

   - **Identyfikator progID**: Identyfikator programowy, czyli ciąg tekstowy, który można używać zamiast identyfikatora GUID.

   - **Wersja**: Używane z ProgID i Coclass, aby wygenerować identyfikator programowy zależne od wersji

1. Kliknij przycisk **Zakończ**.

## <a name="see-also"></a>Zobacz także

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
