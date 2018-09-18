---
title: 'Zestaw rekordów: Uzyskiwanie sum i innych wyników agregacji (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8d78b6375736c35b7a1d49436c870d7f807f6c78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032370"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)

Ten temat dotyczy klas MFC ODBC.  
  
W tym temacie wyjaśniono sposób uzyskiwania agregowanie wyników za pomocą następujących [SQL](../../data/odbc/sql.md) słowa kluczowe:  
  
- **Suma** oblicza sumę wartości w kolumnie z typem danych liczbowych.  
  
- **MIN** wyodrębnia najmniejszą wartość w kolumnie z typem danych liczbowych.  
  
- **Maksymalna liczba** wyodrębnia największą wartość w kolumnie z typem danych liczbowych.  
  
- **Średnia liczba** oblicza wartość średnią wszystkich wartości w kolumnie z typem danych liczbowych.  
  
- **Liczba** zlicza rekordy w kolumnie dowolnego typu danych.  
  
Aby uzyskać informacje statystyczne na temat rekordów w źródle danych, a nie można wyodrębnić rekordy ze źródła danych korzystania z tych funkcji SQL. Zestaw rekordów, które jest zazwyczaj tworzony składa się z pojedynczego rekordu (Jeśli wszystkie kolumny są wartości zagregowane), który zawiera wartość. (Może być więcej niż jeden rekord, jeśli użyto **GROUP BY** klauzuli.) Ta wartość jest wynikiem obliczenia lub wyodrębniania, wykonywane przez funkcję SQL.  
  
> [!TIP]
>  Aby dodać SQL **GROUP BY** — klauzula (i ewentualnie **HAVING** klauzuli) do instrukcji SQL, dołącz go do końca `m_strFilter`. Na przykład:  
  
```  
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";  
```  
  
Można ograniczyć liczbę rekordów, którego używasz do uzyskania agregacji wyników, filtrowanie i sortowanie kolumn.  
  
> [!CAUTION]
>  Niektóre operatory agregacji Zwróć innego typu danych kolumny, w których są agregowania.  
  
- **Suma** i **AVG** może zwrócić następny większy typ danych (na przykład, wywołanie za pomocą `int` zwraca **długie** lub **double**).  
  
- **Liczba** zwykle zwraca **długie** niezależnie od typu kolumny docelowej.  
  
- **Maksymalna liczba** i **MIN** zwracać taki sam typ danych jako kolumny ich obliczania.  
  
     Na przykład **Dodaj klasę** Kreator tworzy `long` `m_lSales` umożliwiających kolumny Sprzedaż, ale trzeba zastąpić za pomocą `double m_dblSumSales` element członkowski danych umożliwiających agregacji wyników. Zobacz poniższy przykład.  
  
#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Aby uzyskać wynik agregacji dla zestawu rekordów  
  
1. Tworzenie zestawu rekordów, zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) zawierająca kolumny, z których chcesz uzyskać agregacji wyników.  
  
1. Modyfikowanie [dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) funkcji dla zestawu rekordów. Zastąp ciąg reprezentujący nazwę kolumny (drugi argument [RFX](../../data/odbc/record-field-exchange-using-rfx.md) wywołaniach funkcji) z ciągu reprezentującego funkcję agregacji w kolumnie. Na przykład Zastąp ciąg:  
  
    ```  
    RFX_Long(pFX, "Sales", m_lSales);  
    ```  
  
     Za pomocą:  
  
    ```  
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)  
    ```  
  
1. Otwórz zestaw rekordów. Wynik operacji agregacji jest pozostawiany w `m_dblSumSales`.  
  
> [!NOTE]
>  Kreator przypisuje faktycznie nazwy elementów członkowskich danych bez Węgierskiej, poprzedź prefiksy. Na przykład Kreator dałby w efekcie `m_Sales` dla kolumny sprzedaży, a nie `m_lSales` nazwę wcześniej używane do celów informacyjnych.  
  
Jeśli używasz [CRecordView](../../mfc/reference/crecordview-class.md) klasy, aby wyświetlić dane, należy zmienić wywołanie funkcji DDX, aby wyświetlić wartość nowy element członkowski danych; w takim przypadku zmianę z:  
  
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