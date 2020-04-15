---
title: 'Wymiana pól rekordów: używanie RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: dc0cdcee758f4842b0738068a8a11c4e2e404155
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367145"
---
# <a name="record-field-exchange-using-rfx"></a>Wymiana pól rekordów: używanie RFX

W tym temacie wyjaśniono, co zrobić, aby użyć RFX w odniesieniu do tego, co robi struktura.

> [!NOTE]
> Ten temat dotyczy klas pochodzących z [CRecordset,](../../mfc/reference/crecordset-class.md) w którym pobieranie wiersza zbiorczego nie zostało zaimplementowane. W przypadku pobierania wierszy zbiorczych zaimplementowana jest zbiorcza wymiana pól rekordów (Bulk RFX). Zbiorczy RFX jest podobny do RFX. Aby zrozumieć różnice, zobacz [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Następujące tematy zawierają powiązane informacje:

- [Wymiana pól rekordów: Praca z kodem kreatora](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) wprowadza główne składniki RFX i wyjaśnia kod, który Kreator aplikacji MFC i **Dodaj klasę** (zgodnie z opisem w [dodanie konsumenta odbc MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) zapisują do obsługi RFX i jak można zmodyfikować kod kreatora.

- [Wymiana pól rekordów: za pomocą funkcji RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) wyjaśnia zapisywanie wywołań do funkcji RFX w `DoFieldExchange` zastąpienie.

W poniższej tabeli przedstawiono swoją rolę w odniesieniu do tego, co robi dla Ciebie ramach.

### <a name="using-rfx-you-and-the-framework"></a>Korzystanie z RFX: Ty i struktura

|Można|Ramy prawne|
|---------|-------------------|
|Deklarowanie klas pliku recordset za pomocą kreatora. Określ nazwy i typy danych elementów członkowskich danych pól.|Kreator wyprowadza `CRecordset` klasę i zapisuje zastąpienie [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) dla Ciebie, w tym wywołanie funkcji RFX dla każdego elementu członkowskiego danych pola.|
|(Opcjonalnie) Ręcznie dodaj wszystkie potrzebne elementy członkowskie danych parametrów do klasy. Ręcznie dodaj wywołanie funkcji RFX `DoFieldExchange` dla każdego elementu członkowskiego danych parametru, dodaj wywołanie do [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) dla grupy parametrów i określ całkowitą liczbę parametrów w [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Zobacz [Recordset: Parametryzacja recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|(Opcjonalnie) Ręcznie powiąż dodatkowe kolumny z elementami elementów członkowskich danych pól. Ręcznie zwiększaj [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Zobacz [Zestaw rekordów: Dynamicznie wiążące kolumny danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Skonstruuj obiekt klasy recordset. Przed użyciem obiektu należy ustawić wartości jego elementów członkowskich danych parametru, jeśli takie istnieją.|Dla wydajności, ramy prebinds parametrów, przy użyciu ODBC. Po przegłosowania wartości parametrów, ramach przekazuje je do źródła danych. Tylko wartości parametrów są wysyłane do ponownegoquerii, chyba że ciągi sortowania i/lub filtru uległy zmianie.|
|Otwórz obiekt zestawu rekordów przy użyciu [CRecordset::Open](../../mfc/reference/crecordset-class.md#open).|Wykonuje kwerendę zestaw rekordów, wiąże kolumny z elementami elementów członkowskich `DoFieldExchange` danych pól zbioru rekordów i wywołuje wymianę danych między pierwszym wybranym rekordem a elementami członkowskich danych pola zbioru rekordów.|
|Przewiń zestaw rekordów za pomocą [CRecordset::Move](../../mfc/reference/crecordset-class.md#move) lub polecenia menu lub paska narzędzi.|Wywołania `DoFieldExchange` przesyłania danych do elementów członkowskich danych pola z nowego bieżącego rekordu.|
|Dodawanie, aktualizowanie i usuwanie rekordów.|Wywołania `DoFieldExchange` przesyłania danych do źródła danych.|

## <a name="see-also"></a>Zobacz też

[Wymiana pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[Makra, funkcje globalne i zmienne globalne](../../mfc/reference/mfc-macros-and-globals.md)
