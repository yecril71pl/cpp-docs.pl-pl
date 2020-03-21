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
ms.openlocfilehash: 38a458eb6634d5075315c9c0bbd2cb215bc76eda
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075901"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)

> [!NOTE]
> Kreator użytkownika ODBC MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono, jak uzyskać agregowane wyniki przy użyciu następujących słów kluczowych [SQL](../../data/odbc/sql.md) :

- **Suma** Oblicza sumę wartości w kolumnie z typem danych liczbowych.

- **Minimum** Wyodrębnia najmniejszą wartość w kolumnie z typem danych liczbowych.

- **Maksymalnie** Wyodrębnia największą wartość w kolumnie z typem danych liczbowych.

- **Średnia** Oblicza średnią wartość wszystkich wartości w kolumnie z typem danych liczbowych.

- **Liczba** Zlicza rekordy w kolumnie dowolnego typu danych.

Te funkcje SQL są używane do uzyskiwania informacji statystycznych dotyczących rekordów w źródle danych, a nie do wyodrębniania rekordów ze źródła danych. Tworzony zestaw rekordów zwykle składa się z pojedynczego rekordu (Jeśli wszystkie kolumny są agregacją), które zawiera wartość. (Może istnieć więcej niż jeden rekord, jeśli użyto klauzuli **Group by** ). Ta wartość jest wynikiem obliczenia lub ekstrakcji wykonywanej przez funkcję SQL.

> [!TIP]
>  Aby dodać klauzulę **Group by** SQL (i ewentualnie klauzulę **HAVING** ) do instrukcji SQL, dołącz ją na końcu `m_strFilter`. Na przykład:

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

Można ograniczyć liczbę rekordów używanych do uzyskania zagregowanych wyników przez filtrowanie i sortowanie kolumn.

> [!CAUTION]
>  Niektóre operatory agregacji zwracają różne typy danych z kolumn, w których są agregowane.

- Funkcja **sum** i **AVG** może zwrócić następny większy typ danych (na przykład wywołanie z `int` zwraca wartość **Long** lub **Double**).

- **Licznik** zwykle zwraca wartość **Long** , niezależnie od typu kolumny docelowej.

- **Max** i **min** zwracają ten sam typ danych co kolumny, które oblicza.

     Na przykład Kreator **dodawania klasy** tworzy `long` `m_lSales` w celu uwzględnienia kolumny Sales, ale trzeba ją zamienić na element członkowski danych `double m_dblSumSales`, aby pomieścić zagregowany wynik. Zobacz poniższy przykład.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Aby uzyskać zagregowany wynik dla zestawu rekordów

1. Utwórz zestaw rekordów zgodnie z opisem w temacie [Dodawanie użytkownika MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) zawierającego kolumny, z których chcesz uzyskać zagregowane wyniki.

1. Zmodyfikuj funkcję [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) dla zestawu rekordów. Zastąp ciąg reprezentujący nazwę kolumny (drugi argument wywołań funkcji [RFX](../../data/odbc/record-field-exchange-using-rfx.md) ) za pomocą ciągu reprezentującego funkcję agregacji w kolumnie. Na przykład Zastąp:

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     tym:

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. Otwórz zestaw rekordów. Wynik operacji agregacji jest pozostawiony w `m_dblSumSales`.

> [!NOTE]
>  Kreator faktycznie przypisuje nazwy składowych danych bez prefiksów węgierskich. Na przykład Kreator wygenerował `m_Sales` dla kolumny Sales, a nie nazwę `m_lSales` użytą wcześniej do ilustracji.

Jeśli używasz klasy [formularzy CRecordView](../../mfc/reference/crecordview-class.md) do wyświetlania danych, musisz zmienić wywołanie funkcji DDX, aby wyświetlić nową wartość elementu członkowskiego danych. w takim przypadku należy zmienić go z:

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