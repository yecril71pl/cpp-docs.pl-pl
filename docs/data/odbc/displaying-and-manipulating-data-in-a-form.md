---
title: Wyświetlanie danych w formularzu i operowanie nimi
ms.date: 11/04/2016
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
ms.openlocfilehash: e50c433e701fbae2e607d79d7abb34efe8eba5b5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033751"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Wyświetlanie danych w formularzu i operowanie nimi

Wiele aplikacji dostęp do danych wybierz dane i wyświetl ją w pól w formularzu. Klasa bazy danych [CRecordView](../../mfc/reference/crecordview-class.md) daje [CFormView](../../mfc/reference/cformview-class.md) obiektu podłączone bezpośrednio do obiektu zestawu rekordów. Używa widoku rekordu [wymiana danych okna dialogowego (DDX)](../../mfc/dialog-data-exchange-and-validation.md) przenoszenia wartości pól bieżącego rekordu w zestawie do kontrolek w formularzu i przenieść zaktualizowane informacje z powrotem do zestawu rekordów. Zestaw rekordów, z kolei używa wymiana pól rekordów (RFX) do przenoszenia danych między jej elementy członkowskie danych pola i odpowiednie kolumny w tabeli w źródle danych.

Można użyć Kreatora aplikacji MFC lub **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) do utworzenia klasa widoku i jego klasa skojarzony zestaw rekordów w połączeniu.

Widoków rekordów i rekordów jego są niszczone, po zamknięciu dokumentu. Aby uzyskać więcej informacji na temat widoków rekordów, zobacz [widoków rekordów](../../data/record-views-mfc-data-access.md). Aby uzyskać więcej informacji na temat RFX zobacz [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Zobacz także

[ODBC i MFC](../../data/odbc/odbc-and-mfc.md)