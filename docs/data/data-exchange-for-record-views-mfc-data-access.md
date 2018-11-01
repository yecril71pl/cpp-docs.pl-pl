---
title: Wymiana danych dla widoków rekordów (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: d3b1c5b997baa0938c532c7a2806d5e65eb125a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546480"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Wymiana danych dla widoków rekordów (dostęp do danych MFC)

Kiedy używasz [Dodaj klasę](../mfc/reference/adding-an-mfc-odbc-consumer.md) do mapy formantów w zasobu szablonu okna dialogowego widoków rekordów do pola zestawu rekordów, szablon zarządza wymiany danych w obu kierunkach — z zestawu rekordów do kontrolek i kontrolki do zestawu rekordów. Przy użyciu mechanizmu DDX oznacza, że nie masz do pisania kodu do przesyłania danych do i z powrotem, samodzielnie.

DDX dla widoków rekordów działa w połączeniu z [RFX](../data/odbc/record-field-exchange-rfx.md) dla zestawów rekordów klasy `CRecordset` (ODBC).  RFX przenosi dane między bieżącego rekordu źródła danych i elementy członkowskie danych pola obiektu zestawu rekordów. DDX przenosi dane z elementy członkowskie danych pola do kontrolek w formularzu. Ta kombinacja wypełnia kontrolek formularza początkowo i przenosi użytkownika między rekordami. Jego można także cofnąć zaktualizowane dane do zestawu rekordów, a następnie ze źródłem danych.

Na poniższej ilustracji przedstawiono relację między DDX i RFX dla widoków rekordów.

![Okno dialogowe&#45;wymiany danych i rejestrowanie&#45;wymiana pól](../data/media/vc37xt1.gif "vc37xt1")<br/>
Wymiana danych okna dialogowego i wymiana pól rekordów

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać więcej informacji na temat RFX zobacz [wymiany pól rekordu (RFX)](../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Zobacz też

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)