---
title: Tworzenie konsumenta bez użycia kreatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a20abb132d0446874b099119dc6c54979aef4638
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023595"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Tworzenie konsumenta bez użycia kreatora

W poniższym przykładzie założono, że dodajesz Obsługa konsumenta OLE DB istniejący projekt ATL. Jeśli chcesz dodać obsługę konsumenta OLE DB dla aplikacji MFC, należy uruchomić Kreatora aplikacji MFC tworzy niezbędne do pomocy technicznej, a następnie wywołuje MFC procedury niezbędne do wykonania aplikacji.  
  
Aby dodać obsługę konsumenta OLE DB bez korzystania z OLE DB Kreator konsumenta ATL:  
  
- Dołącz następujący ciąg w pliku Stdafx.h `#include` instrukcji:  
  
    ```cpp  
    #include <atlbase.h>  
    #include <atldbcli.h>  
    #include <atldbsch.h> // if you are using schema templates  
    ```  
  
Programowo odbiorcy zwykle wykonuje następującą sekwencję czynności:  
  
- Utwórz klasę rekord użytkownika, która wiąże kolumn do zmiennych lokalnych. W tym przykładzie `CMyTableNameAccessor` jest klasa rekordów użytkowników (zobacz [rekordów użytkowników](../../data/oledb/user-records.md)). Ta klasa zawiera kolumny mapy i mapy parametru. Zadeklaruj element członkowski danych w klasie rekordu użytkownika dla każdego pola, którą określisz w mapie kolumny; dla każdej z tych składowych danych należy również zadeklarować element członkowski danych stanu i element członkowski danych długości. Aby uzyskać więcej informacji, zobacz [elementy członkowskie danych stanu pola w metodach dostępu Wizard-Generated](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
    > [!NOTE]
    >  Jeśli piszesz własnego klienta, danych zmienne musi występować przed zmienne stanu i długości.  
  
- Utwórz wystąpienie źródła danych i sesji. Zdecyduj, jakiego typu metody dostępu i zestawu wierszy a, tworzy zestaw wierszy przy użyciu [CCommand](../../data/oledb/ccommand-class.md) lub [CTable](../../data/oledb/ctable-class.md):  
  
    ```cpp  
    CDataSource ds;  
    CSession ss;  
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>  
    ```  
  
- Wywołaj `CoInitialize` zainicjować modelu COM. Zazwyczaj jest to w kodzie głównego. Na przykład:  
  
    ```cpp  
    HRESULT hr = CoInitialize(NULL);  
    ```  
  
- Wywołaj [CDataSource::Open](../../data/oledb/cdatasource-open.md) lub jeden z jego zmiany.  
  
- Otwórz połączenie ze źródłem danych, otwórz sesję i Otwórz i zainicjować zestawu wierszy (i jeśli polecenie również uruchomić go):  
  
    ```cpp  
    hr = ds.Open();  
    hr = ss.Open(ds);  
    hr = rs.Open();            // (Open also executes the command)  
    ```  
  
- Opcjonalnie zestawu wierszy zestaw właściwości za pomocą `CDBPropSet::AddProperty` i przekazywać je jako parametr do `rs.Open`. Aby uzyskać przykład jak to zrobić, zobacz getrowsetproperties — w [metody Consumer Wizard-Generated](../../data/oledb/consumer-wizard-generated-methods.md).  
  
- Można teraz używać zestawu wierszy pobierania/operacje na danych.  
  
- Po zakończeniu aplikacji zamknij połączenie, sesji i zestawu wierszy:  
  
    ```cpp  
    rs.Close();  
    ss.Close();  
    ds.Close();  
    ```  
  
     Jeśli używasz polecenia można wywołać `ReleaseCommand` po `Close`. Przykładowy kod z [CCommand::Close](../../data/oledb/ccommand-close.md) przedstawiono sposób wywoływania `Close` i `ReleaseCommand`.  
  
- Wywołaj `CoUnInitialize` do uninitialize modelu COM. Zazwyczaj jest to w kodzie głównego.  
  
    ```  
    CoUninitialize();  
    ```  
  
## <a name="see-also"></a>Zobacz też  

[Tworzenie konsumenta OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)