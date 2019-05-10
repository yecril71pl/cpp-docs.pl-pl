---
title: Dodawanie konsumenta ATL OLE DB
ms.date: 05/09/2019
helpviewer_keywords:
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
ms.openlocfilehash: 7925063e03522c96d251748b23b6b929733999a1
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524639"
---
# <a name="adding-an-atl-ole-db-consumer"></a>Dodawanie konsumenta ATL OLE DB

::: moniker range="vs-2019"

Kreator OLE DB konsumenta ATL nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach. Można nadal ręcznie dodawać funkcje. Aby uzyskać więcej informacji, zobacz [tworzenie konsumenta bez przy użyciu kreatora](../../data/oledb/creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="vs-2017"

Ten kreator umożliwia dodawanie konsumenta ATL OLE DB do projektu. Konsumenta ATL OLE DB składa się z OLE DB akcesor klasy i powiązania danych konieczne dostępu do źródła danych. Projekt musi być utworzony jako aplikacji ATL COM lub aplikacji Win32 i MFC, która zawiera Obsługa biblioteki ATL, (który automatycznie dodaje OLE DB Kreator konsumenta ATL).

> [!NOTE]
> Konsumenta OLE DB można dodać do projektu MFC. Jeśli to zrobisz, OLE DB Kreator konsumenta ATL dodaje niezbędne Obsługa COM do projektu. Założono, że podczas tworzenia projektu MFC wybrana **formantów ActiveX** pole wyboru (w **funkcje zaawansowane** strony Kreatora aplikacji MFC projektu), która jest domyślnie zaznaczone. Wybranie tej opcji gwarantuje, że aplikacja wywołuje `CoInitialize` i `CoUninitialize`. Jeśli nie wybrano opcji **formantów ActiveX** podczas tworzenia projektu MFC, należy wywołać `CoInitialize` i `CoUninitialize` w kodzie głównego.

## <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>Dodawanie konsumenta ATL OLE DB do projektu

1. W **Widok klas**, kliknij prawym przyciskiem myszy projekt. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj klasę**.

1. W folderze Visual C++, kliknij dwukrotnie **OLE DB konsumenta ATL** ikonę lub wybierz ją i kliknij **Otwórz**.

   Zostanie otwarty Kreator biblioteki ATL OLE DB konsumenta.

1. Zdefiniuj ustawienia, zgodnie z opisem w [OLE DB Kreator konsumenta ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).

1. Kliknij przycisk **Zakończ** aby zamknąć kreatora. Nowo utworzony kod konsumenta OLE DB zostanie wstawiony w projekcie.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)
