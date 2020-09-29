---
title: Tworzenie konsumenta bez użycia kreatora
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: 65add1fe0d47253cd8d7ae7a273286d712ce9db2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500657"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Tworzenie konsumenta bez użycia kreatora

W poniższym przykładzie założono, że dodajesz OLE DB obsługę konsumenta do istniejącego projektu ATL. Jeśli chcesz dodać obsługę OLE DB konsumenta do aplikacji MFC, należy uruchomić **Kreatora aplikacji MFC**, który tworzy wszystkie wymagane wsparcie i wywołuje procedury MFC niezbędne do wykonania aplikacji.

Aby dodać obsługę OLE DB konsumenta bez użycia **kreatora ATL OLE DB użytkownika**:

- W pliku *PCH. h* Dołącz następujące `#include` instrukcje:

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

Programowo, konsument zazwyczaj wykonuje następującą sekwencję operacji:

1. Utwórz klasę rekordów użytkowników, która wiąże kolumny ze zmiennymi lokalnymi. W tym przykładzie `CMyTableNameAccessor` jest klasą rekordów użytkowników (zobacz [rekordy użytkowników](../../data/oledb/user-records.md)). Ta klasa zawiera mapę kolumn i mapę parametrów. Zadeklaruj element członkowski danych w klasie rekordów użytkowników dla każdego pola określonego w mapie kolumn; dla każdego z tych elementów członkowskich danych deklaruje także element członkowski danych stanu i długość elementu członkowskiego danych. Aby uzyskać więcej informacji, zobacz informacje o [stanie pola elementy członkowskie danych w przystawce metod dostępu generowanych przez kreatora](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

    > [!NOTE]
    > W przypadku pisania własnego użytkownika zmienne danych muszą występować przed zmiennymi stan i długość.

- Tworzenie wystąpienia źródła danych i sesji. Zdecyduj, jakiego typu akcesor i zestaw wierszy użyć, a następnie Utwórz wystąpienie zestawu wierszy przy użyciu [CCommand](../../data/oledb/ccommand-class.md) lub [CTable](../../data/oledb/ctable-class.md):

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- Wywołanie `CoInitialize` inicjalizacji com. Jest to wywoływane w kodzie głównym. Na przykład:

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- Wywołanie [CDataSource:: Open](./cdatasource-class.md#open) lub jednej z jej odmian.

- Otwórz połączenie ze źródłem danych, Otwórz sesję i Otwórz i Zainicjuj zestaw wierszy (a także wykonaj również polecenie):

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- Opcjonalnie ustaw właściwości zestawu wierszy przy użyciu `CDBPropSet::AddProperty` i przekaż je jako parametr do `rs.Open` . Aby zapoznać się z przykładem, jak to zrobić, zobacz `GetRowsetProperties` w [metodach generowanych przez kreatora klienta](../../data/oledb/consumer-wizard-generated-methods.md).

- Można teraz używać zestawu wierszy do pobierania i manipulowania danymi.

- Gdy aplikacja jest gotowa, zamknij połączenie, sesję i zestaw wierszy:

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   Jeśli używasz polecenia, możesz chcieć wywołać `ReleaseCommand` po `Close` . Przykład kodu w [CCommand:: Close](./ccommand-class.md#close) pokazuje, jak wywołać `Close` i `ReleaseCommand` .

- Wywołaj metodę `CoUnInitialize` Uninitialize com. Jest to wywoływane w kodzie głównym.

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>Zobacz też

[Tworzenie klienta OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)
