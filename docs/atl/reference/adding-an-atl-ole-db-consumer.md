---
title: Dodawanie konsumenta ATL OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- OLE DB, adding ATL OLE DB consumer to projects
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
ms.openlocfilehash: 467d83413de2666416cc6354bc75c114d178ffb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676918"
---
# <a name="adding-an-atl-ole-db-consumer"></a>Dodawanie konsumenta ATL OLE DB

Ten kreator umożliwia dodawanie konsumenta ATL OLE DB do projektu. Konsumenta ATL OLE DB składa się z OLE DB akcesor klasy i powiązania danych konieczne dostępu do źródła danych. Projekt musi być utworzony jako aplikacji ATL COM lub aplikacji Win32 i MFC, która zawiera Obsługa biblioteki ATL, (który automatycznie dodaje OLE DB Kreator konsumenta ATL).

> [!NOTE]
> Konsumenta OLE DB można dodać do projektu MFC. Jeśli to zrobisz, OLE DB Kreator konsumenta ATL dodaje niezbędne Obsługa COM do projektu. Założono, że podczas tworzenia projektu MFC wybrana **formantów ActiveX** pole wyboru (w **funkcje zaawansowane** strony Kreatora aplikacji MFC projektu), która jest domyślnie zaznaczone. Wybranie tej opcji gwarantuje, że aplikacja wywołuje `CoInitialize` i `CoUninitialize`. Jeśli nie wybrano opcji **formantów ActiveX** podczas tworzenia projektu MFC, należy wywołać `CoInitialize` i `CoUninitialize` w kodzie głównego.

## <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>Dodawanie konsumenta ATL OLE DB do projektu

1. W **Widok klas**, kliknij prawym przyciskiem myszy projekt. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj klasę**.

1. W folderze Visual C++, kliknij dwukrotnie **OLE DB konsumenta ATL** ikonę lub wybierz ją i kliknij **Otwórz**.

   Zostanie otwarty Kreator biblioteki ATL OLE DB konsumenta.

1. Zdefiniuj ustawienia, zgodnie z opisem w [OLE DB Kreator konsumenta ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).

1. Kliknij przycisk **Zakończ** aby zamknąć kreatora. Nowo utworzony kod konsumenta OLE DB zostanie wstawiony w projekcie.

## <a name="see-also"></a>Zobacz też

[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)
