---
title: 'Wymiana pól rekordów: używanie RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 70197d2a9130388e86bb94f0d670360bb35febeb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075870"
---
# <a name="record-field-exchange-using-rfx"></a>Wymiana pól rekordów: używanie RFX

W tym temacie opisano, co należy zrobić, aby użyć RFX w odniesieniu do działania struktury.

> [!NOTE]
>  Ten temat dotyczy klas pochodnych [CRecordset](../../mfc/reference/crecordset-class.md) , w których nie zaimplementowano pobierania wierszy zbiorczych. W przypadku korzystania z pobierania wierszy zbiorczych zaimplementowano wymianę zbiorczych pól rekordów (bulk RFX). RFX Bulk jest podobna do RFX. Aby zrozumieć różnice, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Następujące tematy zawierają informacje pokrewne:

- [Wymiana pól rekordów: Praca z kodem kreatora](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) wprowadza główne składniki RFX i objaśnia kod, który Kreator aplikacji MFC i **dodaje klasę** (zgodnie z opisem w temacie [Dodawanie użytkownika MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) do obsługi RFX i jak można zmodyfikować kod kreatora.

- [Wymiana pól rekordów: Używanie funkcji RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) objaśnia, jak pisać wywołania do funkcji RFX w przesłonięciu `DoFieldExchange`.

W poniższej tabeli przedstawiono rolę w odniesieniu do zawartości platformy.

### <a name="using-rfx-you-and-the-framework"></a>Korzystanie z RFX: ty i struktury

|Można|Struktura programu|
|---------|-------------------|
|Zadeklaruj klasy zestawu rekordów za pomocą kreatora. Określanie nazw i typów danych elementów członkowskich danych pola.|Kreator dziedziczy `CRecordset` klasie i zapisuje przesłonięcie [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) , łącznie z wywołaniem funkcji RFX dla każdego elementu członkowskiego danych pola.|
|Obowiązkowe Ręcznie Dodaj potrzebne elementy członkowskie danych parametrów do klasy. Ręcznie Dodaj wywołanie funkcji RFX do `DoFieldExchange` dla każdego elementu członkowskiego danych parametru, Dodaj wywołanie do [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) dla grupy parametrów i Określ łączną liczbę parametrów w [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Zobacz [zestaw rekordów: parametryzacja a zestaw rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|Obowiązkowe Ręcznie Powiąż dodatkowe kolumny z elementami członkowskimi danych pola. Ręcznie Zwiększ [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Zobacz [zestaw rekordów: dynamiczne wiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Konstruowanie obiektu klasy zestawu rekordów. Przed użyciem obiektu, ustaw wartości jego składowych danych (jeśli istnieją).|W celu zapewnienia wydajności platforma tworzy powiązanie parametrów z użyciem ODBC. Gdy przekazujesz wartości parametrów, struktura przekazuje je do źródła danych. Tylko wartości parametrów są wysyłane do rezapytań, chyba że zostały zmienione ciągi sortowania i/lub filtru.|
|Otwórz obiekt zestawu rekordów przy użyciu [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open).|Wykonuje kwerendę zestawu rekordów, wiąże kolumny z elementami członkowskimi danych pól w zestawie rekordów i wywołuje `DoFieldExchange` do wymiany danych między pierwszym wybranym rekordem a elementami członkowskimi danych pola zestawu rekordów.|
|Przewiń w zestaw rekordów przy użyciu polecenia [CRecordset:: Move](../../mfc/reference/crecordset-class.md#move) lub menu lub paska narzędzi.|Wywołuje `DoFieldExchange` transferu danych do elementów członkowskich danych pola z nowego bieżącego rekordu.|
|Dodawanie, aktualizowanie i usuwanie rekordów.|Wywołuje `DoFieldExchange`, aby przesłać dane do źródła danych.|

## <a name="see-also"></a>Zobacz też

[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[Makra, funkcje globalne i zmienne globalne](../../mfc/reference/mfc-macros-and-globals.md)
