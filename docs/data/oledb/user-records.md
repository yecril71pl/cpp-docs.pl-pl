---
title: Rekordy użytkowników | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_MAP
dev_langs:
- C++
helpviewer_keywords:
- rowsets [C++], accessors
- COLUMN_ENTRY macro
- COLUMN_ENTRY_MAP macro
- user records, OLE DB consumer templates
- OLE DB consumer templates, user records
- CAccessor class, example
- BEGIN_ACCESSOR_MAP macro
- accessors [C++], rowsets
- accessors [C++], static
- BEGIN_ACCESSOR macro, example
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4389fdd35c36a8f7708361176889111b1665f2c6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073657"
---
# <a name="user-records"></a>Rekordy użytkownika

Aby użyć statycznej metody dostępu (oznacza to, że metody dostępu pochodzi od `CAccessor`), konsumentów muszą mieć rekord użytkownika. Rekord użytkownika jest klasy języka C++, który zawiera elementy danych, aby uchwyt dane wejściowe lub wyjściowe. OLE DB Kreator konsumenta ATL generuje rekord użytkownika dla konsumentów. Metody można dodać do rekordu użytkownika dla opcjonalnych zadań, takich jak obsługa poleceń.  
  
Poniższy kod przedstawia rekord przykładowy, który obsługuje polecenia. W rekordzie użytkownika BEGIN_COLUMN_MAP reprezentuje zestawu wierszy danych przekazany klientowi od dostawcy. BEGIN_PARAM_MAP reprezentuje zestaw parametrów polecenia. W tym przykładzie użyto [CCommand](../../data/oledb/ccommand-class.md) klasy, aby obsłużyć parametry polecenia. Elementy członkowskie danych we wpisach w mapie reprezentują przesunięcia w jednym ciągłym bloku pamięci dla każdego wystąpienia klasy. Makra COLUMN_ENTRY odpowiadają makra PROVIDER_COLUMN_ENTRY po stronie dostawcy.  
  
Aby uzyskać więcej informacji na temat COLUMN_MAP i PARAM_MAP makra, zobacz [makra dla OLE DB szablonów konsumentów](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
```cpp  
class CArtists  
{  
public:  
// Data Elements  
   CHAR m_szFirstName[20];  
   CHAR m_szLastName[30];  
   short m_nAge;  
  
// Column binding map  
BEGIN_COLUMN_MAP(CArtists)  
   COLUMN_ENTRY(1, m_szFirstName)  
   COLUMN_ENTRY(2, m_szLastName)  
   COLUMN_ENTRY(3, m_nAge)  
END_COLUMN_MAP()  
  
// Parameter binding map  
BEGIN_PARAM_MAP(CArtists)  
   COLUMN_ENTRY(1, m_nAge)  
END_PARAM_MAP()  
};  
```  
  
## <a name="wizard-generated-user-records"></a>Rekordy generowane przez Kreatora użytkowników  

Możesz generować za pomocą biblioteki ATL OLE DB konsumenta kreatora konsumenta, masz do wyboru używania szablony OLE DB lub OLE DB atrybutów. Wygenerowany kod różni się w każdym przypadku. Aby uzyskać więcej informacji na temat tego kodu, zobacz [klasy Consumer Wizard-Generated](../../data/oledb/consumer-wizard-generated-classes.md).  
  
## <a name="user-record-support-for-multiple-accessors"></a>Obsługa rekordu użytkownika dla wielu metod dostępu  

Aby uzyskać szczegółowe omówienie scenariuszy, w których należy użyć wielu metod dostępu, zobacz [przy użyciu wielu metod dostępu w zestawie wierszy](../../data/oledb/using-multiple-accessors-on-a-rowset.md).  
  
Poniższy przykład przedstawia rekord użytkownika zmodyfikowany w celu obsługi wielu metod dostępu w zestawie wierszy. Zamiast BEGIN_COLUMN_MAP i END_COLUMN_MAP używa [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) i [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) dla każdej metody dostępu. BEGIN_ACCESSOR — makro określa liczbę metody dostępu (przesunięcie od zera) i czy metody dostępu jest autoaccessor. Wywołanie Autoaccessors `GetData` można pobrać dane automatycznie w wywołaniu [MoveNext](../../data/oledb/crowset-movenext.md). Akcesory nonautomatic wymagają jawnie pobierania danych. Użyj nonautomatic metody dostępu są wiązane z polem dużych ilości danych (na przykład obraz mapy bitowej), możesz nie chcieć pobierania dla każdego rekordu.  
  
```cpp  
class CMultiArtists  
{  
public:  
// Data Elements  
   CHAR m_szFirstName[20];  
   CHAR m_szLastName[30];  
   short m_nAge;  
  
// Column binding map  
BEGIN_ACCESSOR_MAP(CMultiArtists, 2)  
   BEGIN_ACCESSOR(0, true)    // true specifies an auto accessor  
    COLUMN_ENTRY(1, m_szFirstName)  
    COLUMN_ENTRY(2, m_szLastName)  
   END_ACCESSOR()  
   BEGIN_ACCESSOR(1, false)   // false specifies a manual accessor  
    COLUMN_ENTRY(3, m_nAge)  
   END_ACCESSOR()  
END_ACCESSOR_MAP()  
};  
```  
  
## <a name="see-also"></a>Zobacz też  

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)