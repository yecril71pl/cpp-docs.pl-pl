---
title: 'Wymiana pól rekordów: Używanie RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 2a029f653753363e08b3c4f8b9fceab6295924af
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034118"
---
# <a name="record-field-exchange-using-rfx"></a>Wymiana pól rekordów: Używanie RFX

W tym temacie opisano, co zrobić, aby użyć RFX względem działanie platformę.

> [!NOTE]
>  Ten temat dotyczy klasy pochodne [CRecordset](../../mfc/reference/crecordset-class.md) w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza zbiorcza wymiana pól rekordów (zbiorcze RFX) jest zaimplementowana. Zbiorcze RFX przypomina RFX. Aby poznać różnice, zobacz [zestaw rekordów: Pobieranie rekordów (ODBC) zbiorcze](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Informacje pokrewne można znaleźć w następujących tematach:

- [Wymiana pól rekordów: Praca z kodem kreatora](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) wprowadza główne składniki RFX oraz wyjaśniono kod, Kreator aplikacji MFC i **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) zapisu Aby obsługiwać RFX i jak możesz chcieć zmodyfikować kod kreatora.

- [Wymiana pól rekordów: Używanie funkcji RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) wyjaśnia pisania wywołania funkcji RFX w swojej `DoFieldExchange` zastąpienia.

W poniższej tabeli przedstawiono Twoja rola względem struktura jest dla Ciebie.

### <a name="using-rfx-you-and-the-framework"></a>Używanie RFX: Użytkownik i struktury

|Można|Struktura|
|---------|-------------------|
|Deklarowanie klas zestawu rekordów za pomocą kreatora. Określ nazwy i typy danych elementów członkowskich danych pola.|Kreator pochodzi `CRecordset` klasy i zapisy [dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) zastąpienia dla Ciebie, łącznie z RFX wywołania funkcji dla każdego elementu członkowskiego danych pola.|
|(Opcjonalnie) Ręcznie Dodaj żadnych składowych danych wymaganego parametru do klasy. Ręcznie dodaj wywołanie funkcji RFX `DoFieldExchange` dla każdego elementu członkowskiego danych parametru Dodaj wywołanie [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) grupy parametrów i określ łączna liczba parametrów w [m_nparams — ](../../mfc/reference/crecordset-class.md#m_nparams). Zobacz [zestaw rekordów: Parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|(Opcjonalnie) Ręcznie powiązać dodatkowe kolumny elementy członkowskie danych pola. Ręcznie zwiększyć [m_nfields —](../../mfc/reference/crecordset-class.md#m_nfields). Zobacz [zestaw rekordów: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Skonstruuj obiekt klasy zestawu rekordów. Przed rozpoczęciem korzystania z obiektu ustawić wartości tego parametru składowe danych, jeśli istnieją.|W celu zwiększenia wydajności w ramach prebinds parametrów, przy użyciu interfejsu ODBC. Jeśli przekazujesz wartości parametrów, struktura przekazuje je do źródła danych. Nie będą wysyłane tylko wartości parametrów dla requeries, sortowania i/lub filtru ciągów uległy zmianie.|
|Otwórz obiekt zestawu rekordów przy użyciu [CRecordset::Open](../../mfc/reference/crecordset-class.md#open).|Wykonuje zapytanie w zestawie rekordów, wiąże kolumny elementy członkowskie danych pola zestawu rekordów i wywołania `DoFieldExchange` wymianę danych między pierwszym wybranego rekordu i elementy członkowskie danych pola w zestawie rekordów.|
|Przewiń w zestawie rekordów za pomocą [CRecordset::Move](../../mfc/reference/crecordset-class.md#move) lub polecenie menu lub paska narzędzi.|Wywołania `DoFieldExchange` na przesyłanie danych do elementy członkowskie danych pola z bieżącego rekordu.|
|Dodawać, aktualizować i usuwać rekordy.|Wywołania `DoFieldExchange` na przesyłanie danych do źródła danych.|

## <a name="see-also"></a>Zobacz także

[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Wymiana pól rekordów: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Zestaw rekordów: Uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[Makra, funkcje globalne i zmienne globalne](../../mfc/reference/mfc-macros-and-globals.md)

