---
title: Elementy członkowskie dotyczące stanu pola w metodach dostępu generowanych przez kreatora
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: 46cf285e07bffe178874546d13d196b5165cb28b
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524361"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Elementy członkowskie dotyczące stanu pola w metodach dostępu generowanych przez kreatora

Kiedy używasz **OLE DB Kreator konsumenta ATL** Aby utworzyć odbiorcę, Kreator generuje element członkowski danych w klasie rekordu użytkownika dla każdego pola, które określisz w mapie kolumny. Każdy element członkowski danych jest typu `DWORD` i zawiera wartość stanu, odpowiadający jej odpowiednich pól.

Na przykład element członkowski danych *m_OwnerID*, Kreator generuje elementu członkowskiego dodatkowe dane dotyczące stanu pola (*dwOwnerIDStatus*) a innym, długość pola (*dwOwnerIDLength*). Generuje mapę kolumny z wpisy COLUMN_ENTRY_LENGTH_STATUS.

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
> Jeśli modyfikujesz klasy rekordu użytkownika lub napisać własny konsumenta, zmiennych danych musi występować przed zmienne stanu i długości.

Wartości stanu można użyć na potrzeby debugowania. Jeśli kod wygenerowany przez **OLE DB Kreator konsumenta ATL** generuje błędy kompilacji takich jak DB_S_ERRORSOCCURRED lub DB_E_ERRORSOCCURRED, należy najpierw przyjrzymy się bieżących wartości pól elementy członkowskie dotyczące stanu. Te, które mają różną od zera wartości odpowiadają naruszającym kolumn.

Można również użyć wartości stanu, można ustawić wartości NULL dla określonego pola. Pomoże w przypadkach, w których chcesz rozróżnienie wartości pola jako wartość NULL, a nie wartość zero. Jest podjęcie decyzji o wartości NULL, jest prawidłową wartością lub wartością specjalną, i zdecyduj, jak aplikacja powinna obsługiwać go. OLE DB definiuje DBSTATUS_S_ISNULL jako prawidłowy sposób określania ogólnej wartości NULL. Jeśli odbiorca odczytuje dane i ma wartość null, w polu stanu jest równa DBSTATUS_S_ISNULL. Jeśli użytkownik chce, aby ustawić wartość NULL, użytkownik ustawia wartość stanu DBSTATUS_S_ISNULL przed wywołaniem dostawcy.

Następnie otwórz Oledb.h i wyszukaj DBSTATUSENUM. Następnie można dopasować liczbową wartość różną od zera stanu dla DBSTATUSENUM wartości wyliczenia. Jeśli nazwa wyliczenia nie są wystarczające do informujące o tym, czym jest problem, zobacz **stan** tematu w **powiązania wartości danych** części [OLE DB przewodnik](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Ten temat zawiera tabele wartości stanu używany podczas pobierania lub ustawiania danych. Aby uzyskać informacji na temat wartości długości, zobacz **długość** tematu w tej samej sekcji.

## <a name="retrieving-the-length-or-status-of-a-column"></a>Pobieranie długości lub stan kolumny

Możesz pobrać długość kolumny zmiennej długości lub stan kolumny (w celu sprawdzania DBSTATUS_S_ISNULL, na przykład):

- Aby uzyskać długości, użyj COLUMN_ENTRY_LENGTH — makro.

- Aby uzyskać stan, użyj COLUMN_ENTRY_STATUS — makro.

- Aby uzyskać zarówno, należy użyć COLUMN_ENTRY_LENGTH_STATUS, jak pokazano:

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

- Następnie uzyskać dostęp do długości i/lub stan jak pokazano:

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

Kiedy używasz `CDynamicAccessor`, długość i stanu są powiązane dla Ciebie automatycznie. Aby pobrać wartości długości i stanu, użyj `GetLength` i `GetStatus` funkcji elementów członkowskich.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)