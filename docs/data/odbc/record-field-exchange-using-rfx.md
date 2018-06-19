---
title: 'Wymiana pól rekordów: Używanie RFX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 296ae2e4f535e08924a77b8726b93778a6da5026
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092001"
---
# <a name="record-field-exchange-using-rfx"></a>Wymiana pól rekordów: używanie RFX
W tym temacie wyjaśniono, co zrobić, aby użyć RFX w odniesieniu do czego platformę.  
  
> [!NOTE]
>  Ten temat dotyczy klasy pochodzące od [crecordset —](../../mfc/reference/crecordset-class.md) w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza zbiorcza wymiana pól rekordów (RFX zbiorczego) jest zaimplementowana. Zbiorcze RFX jest podobny do RFX. Aby poznać różnice, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Informacje pokrewne można znaleźć w następujących tematach:  
  
-   [Wymiana pól rekordów: Praca z kodem kreatora](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) wprowadzono głównymi składnikami RFX i opisano kod który Kreator aplikacji MFC i **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta MFC ODBC ](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) zapisu do obsługi RFX i jak można zmodyfikować kod kreatora.  
  
-   [Wymiana pól rekordów: Używanie funkcji RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) wyjaśniono pisania wywołania funkcji RFX w Twojej `DoFieldExchange` zastąpienia.  
  
 W poniższej tabeli przedstawiono swojej roli w ramach jest dla Ciebie.  
  
### <a name="using-rfx-you-and-the-framework"></a>Używanie RFX: Użytkownik i struktura  
  
|Można|Platformę|  
|---------|-------------------|  

| Deklarowanie klas rekordów za pomocą kreatora. Określanie nazwy i typy danych elementy członkowskie danych pola. | Kreator pochodzi `CRecordset` klasy, jak i zapisów [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) zastępowania dla Ciebie, łącznie z RFX wywołania funkcji dla każdego elementu członkowskiego danych pola. |  
| (Opcjonalnie) Ręcznie Dodaj wszystkie elementy członkowskie danych parametru potrzebne do klasy. Ręcznie dodaj wywołanie funkcji RFX `DoFieldExchange` dla każdego elementu członkowskiego danych parametru Dodaj wywołanie do [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) grupy parametry i określ całkowita liczba parametrów w [m_nparams — ](../../mfc/reference/crecordset-class.md#m_nparams). Zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md). ||  
| (Opcjonalnie) Elementy członkowskie danych pola ręcznie powiązać dodatkowych kolumn. Ręcznie zwiększyć [m_nfields —](../../mfc/reference/crecordset-class.md#m_nfields). Zobacz [zestaw rekordów: dynamiczne wiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). ||  

| Utworzyć obiekt klasy zestawu rekordów. Przed użyciem obiektu, ustaw wartości jego parametru elementy członkowskie danych, jeśli istnieje. | W celu zwiększenia wydajności w ramach prebinds parametrów, za pośrednictwem sterownika ODBC. Jeśli wartości parametrów, platformę przekazuje je do źródła danych. Tylko wartości parametrów są wysyłane requeries, chyba że zmieniono ciągi sortowania i/lub filtr. |  
| Otwórz obiekt zestawu rekordów za pomocą [CRecordset::Open](../../mfc/reference/crecordset-class.md#open). | Wykonuje zapytanie w zestawie rekordów, wiąże kolumn elementy członkowskie danych pola rekordów i wywołania `DoFieldExchange` do wymiany danych między pierwszym wybranego rekordu i elementy członkowskie danych pola w zestawie rekordów. |  
| Przewijania w zestawie rekordów przy użyciu [CRecordset::Move](../../mfc/reference/crecordset-class.md#move) lub polecenia menu lub pasek narzędzi. | Wywołania `DoFieldExchange` na przesyłanie danych do elementy członkowskie danych pola z bieżącego rekordu. |  
| Dodawanie, aktualizowanie i usuwanie rekordów. | Wywołania `DoFieldExchange` na przesyłanie danych do źródła danych. |  
  
## <a name="see-also"></a>Zobacz też  
 [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [Wymiana pól rekordów: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [Zestaw rekordów: Uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [Crecordset — klasa](../../mfc/reference/crecordset-class.md)   
 [Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)   
 [Makra, funkcje globalne i zmienne globalne](../../mfc/reference/mfc-macros-and-globals.md)

