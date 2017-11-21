---
title: "Zestaw rekordów: Uzyskiwanie sum i innych wyników agregacji (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f69341095e2bf6ad97e3b9c3fa0535c349c47ca3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W tym temacie wyjaśniono sposób uzyskiwania wyników agregacji, użycie następujących [SQL](../../data/odbc/sql.md) słowa kluczowe:  
  
-   **Suma** oblicza sumę wartości w kolumnie z dane typu liczbowego.  
  
-   **MIN** wyodrębnia najmniejszą wartość w kolumnie z dane typu liczbowego.  
  
-   **Maksymalna liczba** wyodrębnia największą wartość w kolumnie z dane typu liczbowego.  
  
-   **Średni** oblicza wartość średnią wszystkich wartości w kolumnie z dane typu liczbowego.  
  
-   **Liczba** zlicza rekordów w kolumnie każdego typu danych.  
  
 Aby uzyskać informacje statystyczne na temat rekordów w źródle danych, a nie można wyodrębnić rekordy ze źródła danych korzystania z tych funkcji SQL. Zestaw rekordów, które jest tworzone zazwyczaj składa się z pojedynczego rekordu (Jeśli wszystkie kolumny są wartości zagregowanych), który zawiera wartość. (Może być więcej niż jeden rekord, jeśli używasz **GROUP BY** klauzuli.) Ta wartość jest wynikiem obliczenia lub wyodrębniania wykonywane przez funkcję SQL.  
  
> [!TIP]
>  Aby dodać SQL **GROUP BY** klauzuli (i prawdopodobnie **HAVING** klauzuli) do instrukcji SQL, dołącz go do końca **m_strFilter**. Na przykład:  
  
```  
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";  
```  
  
 Można ograniczyć liczbę rekordów, które umożliwia uzyskanie wyników agregacji przez filtrowanie i sortowanie kolumny.  
  
> [!CAUTION]
>  Niektóre operatorów agregacji zwrócić na inny typ danych kolumny, w których są agregowanie.  
  
-   **Suma** i **AVG** może zwrócić następny większy typ danych (na przykład wywoływanie z `int` zwraca **DŁUGI** lub **podwójne**).  
  
-   **Liczba** zwykle zwraca **DŁUGI** niezależnie od typu kolumny docelowej.  
  
-   **Maksymalna liczba** i **MIN** zwracać taki sam typ danych jak kolumny ich obliczania.  
  
     Na przykład **Dodaj klasę** Kreator tworzy `long` `m_lSales` aby zmieścił się w kolumnie sprzedaży, ale należy zamienić na ten z `double m_dblSumSales` element członkowski danych w celu uwzględnienia łączny wynik. Zobacz poniższy przykład.  
  
#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Aby uzyskać wynik agregacji dla zestawu rekordów  
  
1.  Tworzenie zestawu rekordów, zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) zawierającą kolumny, z których chcesz uzyskać wyników agregacji.  
  
2.  Modyfikowanie [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) funkcji zestawu rekordów. Zastąp ciąg reprezentujący nazwę kolumny (drugi argument funkcji [RFX](../../data/odbc/record-field-exchange-using-rfx.md) wywołania funkcji) z ciąg reprezentujący funkcją agregacji w kolumnie. Zamień na przykład:  
  
    ```  
    RFX_Long(pFX, "Sales", m_lSales);  
    ```  
  
     Z:  
  
    ```  
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)  
    ```  
  
3.  Otwórz zestaw rekordów. Wynik operacji agregacji pozostanie w `m_dblSumSales`.  
  
> [!NOTE]
>  Kreator przypisuje faktycznie nazwy elementów członkowskich danych bez Węgierskiej prefiksy. Na przykład Kreator dałby w efekcie `m_Sales` dla kolumny sprzedaży, a nie `m_lSales` nazwa używana wcześniej na ilustracji.  
  
 Jeśli używasz [CRecordView](../../mfc/reference/crecordview-class.md) klasy, aby wyświetlić dane, trzeba zmienić wywołanie funkcji DDX, aby wyświetlić nową wartość elementu członkowskiego danych; w przypadku zmiany z poziomu:  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);  
```  
  
 Do:  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)