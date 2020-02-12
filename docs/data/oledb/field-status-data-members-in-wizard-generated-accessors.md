---
title: Elementy członkowskie dotyczące stanu pola w metodach dostępu generowanych przez kreatora
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: 41be62627d79c7207816818f09956a60e8b3facc
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127652"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Elementy członkowskie dotyczące stanu pola w metodach dostępu generowanych przez kreatora

::: moniker range="vs-2019"

Kreator użytkownika ATL OLE DB nie jest dostępny w programie Visual Studio 2019 i nowszych. Można nadal ręcznie dodawać funkcje. Aby uzyskać więcej informacji, zobacz [Tworzenie klienta bez korzystania z Kreatora](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

W przypadku utworzenia konsumenta przy użyciu **kreatora ATL OLE DB** User, Kreator generuje element członkowski danych w klasie rekordu użytkownika dla każdego pola określonego w mapie kolumn. Każdy element członkowski danych jest typu `DWORD` i zawiera wartość stanu odpowiadającą jej odpowiedniemu polu.

Na przykład dla elementu członkowskiego danych *m_OwnerID*Kreator generuje dodatkowy element członkowski danych dla stanu pola (*dwOwnerIDStatus*), a drugi dla długości pola (*dwOwnerIDLength*). Generuje również mapę kolumn zawierającą COLUMN_ENTRY_LENGTH_STATUS wpisów.

Jest to pokazane w poniższym kodzie:

```cpp
class CAuthorsAccessor
{
public:
   LONG m_AuID;
   TCHAR m_Author[53];
   LONG m_YearBorn;

   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;

   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;

   DEFINE_COMMAND_EX(CAuthorsAccessor, L" \
   SELECT \
      AuID, \
      Author, \
      YearBorn \
      FROM dbo.Authors")

   BEGIN_COLUMN_MAP(CAuthorsAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)
   END_COLUMN_MAP()
...
```

> [!NOTE]
> W przypadku modyfikacji klasy rekordu użytkownika lub napisania własnego odbiorcy zmienne danych muszą występować przed zmiennymi stan i długość.

Wartości stanu można użyć do celów debugowania. Jeśli kod wygenerowany przez **kreatora ATL OLE DB użytkownika** generuje błędy kompilacji, takie jak DB_S_ERRORSOCCURRED lub DB_E_ERRORSOCCURRED, należy najpierw przejrzeć bieżące wartości elementów członkowskich danych stanu pola. Te, które mają wartość różną od zera, odpowiadają kolumnom, które są nieprawidłowe.

Można również użyć wartości stanu, aby ustawić wartość NULL dla określonego pola. Dzięki temu można w przypadkach, w których chcesz odróżnić wartość pola jako wartość NULL, a nie zero. Istnieje możliwość określenia, czy wartość NULL jest prawidłowa, czy wartość specjalna i decyduje o tym, jak aplikacja powinna ją obsłużyć. OLE DB definiuje DBSTATUS_S_ISNULL jako poprawna Metoda określania ogólnej wartości NULL. Jeśli konsument odczytuje dane, a wartość jest równa null, pole stanu ma wartość DBSTATUS_S_ISNULL. Jeśli odbiorca chce ustawić wartość NULL, konsument ustawi wartość stanu na DBSTATUS_S_ISNULL przed wywołaniem dostawcy.

Następnie otwórz OLEDB. h i wyszukaj ciąg DBSTATUSENUM. Następnie można dopasować wartość numeryczną stanu niezerowego do wartości wyliczenia DBSTATUSENUM. Jeśli nazwa wyliczenia nie jest wystarczająca do poinformowania o błędach, zobacz temat **stan** w sekcji **wartości danych powiązania** w [przewodniku OLE DB programisty](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Ten temat zawiera tabele wartości stanu używanych podczas pobierania lub ustawiania danych. Aby uzyskać informacje na temat długości wartości, zobacz temat **Długość** w tej samej sekcji.

## <a name="retrieving-the-length-or-status-of-a-column"></a>Pobieranie długości lub stanu kolumny

Można pobrać długość kolumny o zmiennej długości lub stanu kolumny (na przykład w celu sprawdzenia, czy DBSTATUS_S_ISNULL):

- Aby uzyskać długość, użyj makra COLUMN_ENTRY_LENGTH.

- Aby uzyskać stan, użyj makra COLUMN_ENTRY_STATUS.

- Aby skorzystać z obu tych metod, użyj COLUMN_ENTRY_LENGTH_STATUS, jak pokazano poniżej:

    ```cpp
    class CProducts
    {
    public:
       char      szName[40];
       long      nNameLength;
       DBSTATUS   nNameStatus;

    BEGIN_COLUMN_MAP(CProducts)
    // Bind the column to CProducts.m_ProductName.
    // nOrdinal is zero-based, so the column number of m_ProductName is 1.
       COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)
    END_COLUMN_MAP()
    };
    ```

- Następnie uzyskaj dostęp do podanej długości i/lub stanu:

    ```cpp
    CTable<CAccessor<CProducts >> product;
    CSession session;

    product.Open(session, "Product");

    while (product.MoveNext() == S_OK)
    {
       // Check the product name isn't NULL before tracing it
       if (product.nNameStatus == DBSTATUS_S_OK)
          ATLTRACE("%s is %d characters\n", product.szName, product.nNameLength);
    }
    ```

W przypadku używania `CDynamicAccessor`długość i stan są powiązane automatycznie. Aby pobrać wartości długości i stanu, użyj `GetLength` i `GetStatus` funkcji Członkowskich.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)