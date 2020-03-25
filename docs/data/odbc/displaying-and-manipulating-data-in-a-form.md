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
ms.openlocfilehash: 6b663fabd0c87d9a2773e6f5a2796bcc8f57ce29
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213255"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Wyświetlanie danych w formularzu i operowanie nimi

Wiele aplikacji dostępu do danych wybiera dane i wyświetla je w polach formularza. Klasa bazy danych [formularzy CRecordView](../../mfc/reference/crecordview-class.md) zapewnia obiekt [CFormView](../../mfc/reference/cformview-class.md) bezpośrednio połączony z obiektem zestawu rekordów. Widok rekordu używa [wymiany danych okna dialogowego (DDX)](../../mfc/dialog-data-exchange-and-validation.md) do przenoszenia wartości pól bieżącego rekordu z zestawu rekordów do kontrolek w formularzu i przenoszenia zaktualizowanych informacji z powrotem do zestawu rekordów. Zestaw rekordów, z kolei używa wymiany pól rekordów (RFX) do przenoszenia danych między elementami członkowskimi danych pola i odpowiednimi kolumnami w tabeli w źródle danych.

Można użyć Kreatora aplikacji MFC lub **dodać klasę** (zgodnie z opisem w temacie [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) do utworzenia klasy widoku i skojarzonej z nią klasy zestawu rekordów w połączeniu.

Widok rekordu i jego zestaw rekordów są niszczone po zamknięciu dokumentu. Aby uzyskać więcej informacji na temat widoków rekordów, zobacz [widoki rekordów](../../data/record-views-mfc-data-access.md). Aby uzyskać więcej informacji na temat RFX, zobacz [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Zobacz też

[ODBC i MFC](../../data/odbc/odbc-and-mfc.md)
