---
title: 'Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
ms.openlocfilehash: 9ebbe78191d0c4140baf3557637ba2103886577d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368655"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)

> [!NOTE]
> Kreator konsumenta odbc MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono, jak uzyskać wyniki agregacji przy użyciu następujących słów kluczowych [SQL:](../../data/odbc/sql.md)

- **SUMA** Oblicza sumę wartości w kolumnie z typem danych liczbowych.

- **Min.** Wyodrębnia najmniejszą wartość w kolumnie z typem danych liczbowych.

- **MAKS.** Wyodrębnia największą wartość w kolumnie z typem danych liczbowych.

- **Avg (właśc.** Oblicza średnią wartość wszystkich wartości w kolumnie z typem danych liczbowych.

- **ZLICZANIE** Zlicza liczbę rekordów w kolumnie dowolnego typu danych.

Te funkcje SQL służy do uzyskiwania informacji statystycznych o rekordach w źródle danych, a nie wyodrębnić rekordy ze źródła danych. Utworzony plan records zwykle składa się z pojedynczego rekordu (jeśli wszystkie kolumny są agregacjami), który zawiera wartość. (Jeśli użyto klauzuli **GROUP BY,** może istnieć więcej niż jeden rekord). Ta wartość jest wynikiem obliczeń lub ekstrakcji wykonywanych przez funkcję SQL.

> [!TIP]
> Aby dodać klauzulę SQL **GROUP BY** (i ewentualnie klauzulę **HAVING)** do `m_strFilter`instrukcji SQL, dołącz ją na końcu . Przykład:

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

Można ograniczyć liczbę rekordów używanych do uzyskiwania wyników agregacji przez filtrowanie i sortowanie kolumn.

> [!CAUTION]
> Niektóre operatory agregacji zwracają inny typ danych z kolumn, za którymi są agregowane.

- **SUMA** i **AVG** mogą zwracać następny większy `int` typ danych (na przykład wywołanie z zwrotami **LONG** lub **double).**

- **LICZBA** zwykle zwraca **LONG** niezależnie od typu kolumny docelowej.

- **MAX** i **MIN** zwracają ten sam typ danych, co kolumny, które obliczają.

     Na przykład Kreator **dodawania klasy** tworzy, `long` `m_lSales` aby pomieścić Sales kolumny, `double m_dblSumSales` ale trzeba zastąpić to element członkowski danych, aby pomieścić wynik agregacji. Zobacz poniższy przykład.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Aby uzyskać wynik zagregowany dla zestawie rekordów

1. Utwórz zestawie rekordów zgodnie z opisem w [Dodawanie konsumenta odbc MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) zawierający kolumny, z których chcesz uzyskać wyniki agregacji.

1. Zmodyfikuj funkcję [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) dla pliku recordset. Zastąp ciąg reprezentujący nazwę kolumny (drugi argument wywołania funkcji [RFX)](../../data/odbc/record-field-exchange-using-rfx.md) ciągiem reprezentującym funkcję agregacji w kolumnie. Na przykład zamień:

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     tym:

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. Otwórz apecję. Wynik operacji agregacji pozostaje `m_dblSumSales`w pliku .

> [!NOTE]
> Kreator faktycznie przypisuje nazwy elementów członkowskich danych bez prefiksów węgierskich. Na przykład kreator będzie `m_Sales` tworzyć dla sales kolumny, a nie `m_lSales` nazwę używaną wcześniej do ilustracji.

Jeśli używasz [CRecordView](../../mfc/reference/crecordview-class.md) klasy do wyświetlania danych, należy zmienić wywołanie funkcji DDX, aby wyświetlić nową wartość elementu członkowskiego danych; w takim przypadku, zmieniając go z:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

Do:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
