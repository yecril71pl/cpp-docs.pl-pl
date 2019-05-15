---
title: Dodawanie dostawcy ATL OLE DB
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, adding ATL OLE DB provider to projects
- ATL projects, adding ATL OLE DB providers
- ATL OLE DB providers
ms.assetid: 26fba1e3-880f-4bc6-90e5-2096a48a3a6c
ms.openlocfilehash: 36c07da6249a106836433e127f95258d4ed5b509
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706944"
---
# <a name="adding-an-atl-ole-db-provider"></a>Dodawanie dostawcy ATL OLE DB

::: moniker range="vs-2019"

Kreator ATL OLE DB Provider nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="<=vs-2017"

Ten kreator umożliwia dodawanie dostawcy ATL OLE DB do projektu. Dostawcy ATL OLE DB składa się z źródła danych, sesji, polecenie i klasy zestawów wierszy. Projekt musi być utworzony jako aplikacji ATL COM.

## <a name="to-add-an-atl-ole-db-provider-to-your-project"></a>Dodawanie dostawcy ATL OLE DB do projektu

1. W **Widok klas**, kliknij prawym przyciskiem myszy projekt. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj klasę**.

1. W **Visual C++** folderu, kliknij dwukrotnie **ATL OLE DB Provider** ikonę lub wybierz ją i kliknij **Otwórz**.

   Zostanie otwarty Kreator biblioteki ATL OLE DB Provider.

1. Zdefiniuj ustawienia, zgodnie z opisem w [Kreator biblioteki ATL OLE DB Provider](../../atl/reference/atl-ole-db-provider-wizard.md).

1. Kliknij przycisk **Zakończ** aby zamknąć kreatora, który powoduje wstawienie nowo utworzony kod dostawcy OLE DB w projekcie.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)
