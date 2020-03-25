---
title: Wymiana danych dla widoków rekordów (dostęp do danych MFC)
ms.date: 11/19/2018
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: f9f460305b55a2313b64effdf4d1dbbfd9823def
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213476"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Wymiana danych dla widoków rekordów (dostęp do danych MFC)

Gdy używasz [Dodaj klasy](../mfc/reference/adding-an-mfc-odbc-consumer.md) do mapowania formantów w zasobów szablonu okna dialogowego widoku rekordu do pól zestawu rekordów, struktura zarządza wymianą danych w obu kierunkach — od zestawu rekordów do formantów i z formantów do zestawu rekordów. Użycie mechanizmu DDX oznacza, że nie trzeba pisać kodu w celu samodzielnego przesyłania danych.

DDX dla widoków rekordów działa w połączeniu z [RFX](../data/odbc/record-field-exchange-rfx.md) dla zestawów rekordów klasy `CRecordset` (ODBC).  RFX przenosi dane między bieżącym rekordem źródła danych i danymi pól w obiekcie zestawu rekordów. DDX przenosi dane z elementów członkowskich danych pola do kontrolek w formularzu. Ta kombinacja automatycznie wypełnia kontrolki formularza i, gdy użytkownik przechodzi z rekordu do rekordu. Umożliwia również przeniesienie zaktualizowanych danych z powrotem do zestawu rekordów, a następnie do źródła danych.

Na poniższej ilustracji przedstawiono relacje między DDX i RFX dla widoków rekordów.

![Wymiana&#45;danych okna dialogowego i&#45;wymiana pól rekordów](../data/media/vc37xt1.gif "Wymiana&#45;danych okna dialogowego i&#45;wymiana pól rekordów")<br/>
Wymiana danych okna dialogowego i wymiana pól rekordów

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać więcej informacji na temat RFX, zobacz [wymiany pól rekordów (RFX)](../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Zobacz też

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)
