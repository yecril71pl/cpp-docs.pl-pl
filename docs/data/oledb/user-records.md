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
ms.openlocfilehash: aea6b4b2ebb1a02e4ef669b437fbe7eb30937f9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109810"
---
# <a name="user-records"></a>Rekordy użytkownika
Aby użyć statycznej metody dostępu (czyli metody dostępu pochodzi od **CAccessor)**, Twoje konsumenta muszą mieć rekord użytkownika. Rekord użytkownika jest klasę C++, która zawiera elementy danych do obsługi danych wejściowych lub wyjściowych. OLE DB Kreator konsumenta ATL generuje rekord użytkownika dla użytkownika konsumenta. Metody można dodać do rekordu użytkownika, która ma być opcjonalne zadania, takie jak obsługa poleceń.  
  
 Poniższy kod przedstawia przykładowy rekord, który obsługuje poleceń. W rekordzie użytkownika `BEGIN_COLUMN_MAP` reprezentuje zestawu wierszy danych przekazany do użytkownika od dostawcy. `BEGIN_PARAM_MAP` reprezentuje zestaw parametrów polecenia. W tym przykładzie użyto [CCommand](../../data/oledb/ccommand-class.md) klasę, aby obsłużyć parametry polecenia. Elementy członkowskie danych w wpisy mapy reprezentują przesunięcia do jednego ciągłego bloku pamięci dla każdego wystąpienia klasy. `COLUMN_ENTRY` Makra odpowiadają `PROVIDER_COLUMN_ENTRY` makra po stronie dostawcy.  
  
 Aby uzyskać więcej informacji na temat **COLUMN_MAP** i **atrybut PARAM_MAP** makra, zobacz [makra dla OLE DB szablonów konsumentów](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
```  
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
  
## <a name="wizard-generated-user-records"></a>Rekordy użytkowników generowane przez kreatora  
 Jeśli używasz OLE DB Kreator konsumenta ATL do generowania konsumenta, jest to możliwe przy użyciu szablonów OLE DB lub OLE DB atrybutów. Wygenerowany kod różni się w każdym przypadku. Aby uzyskać więcej informacji o tym kodzie, zobacz [Consumer Wizard-Generated klasy](../../data/oledb/consumer-wizard-generated-classes.md).  
  
## <a name="user-record-support-for-multiple-accessors"></a>Obsługa rekordu użytkownika dla wielu metod dostępu  
 Szczegółowe omówienie scenariuszy, w których należy użyć wielu metod dostępu, zobacz [przy użyciu wielu metod dostępu w zestawie wierszy](../../data/oledb/using-multiple-accessors-on-a-rowset.md).  
  
 W poniższym przykładzie przedstawiono rekordu użytkownika, zmodyfikowany w celu obsługi wielu metod dostępu w zestawie wierszy. Zamiast `BEGIN_COLUMN_MAP` i `END_COLUMN_MAP`, używa [begin_accessor_map —](../../data/oledb/begin-accessor-map.md) i [begin_accessor —](../../data/oledb/begin-accessor.md) dla każdej metody dostępu. `BEGIN_ACCESSOR` Makro określa numer metody dostępu (przesunięcie od zera) oraz czy jest autoaccessor w metodzie dostępu. Wywołanie Autoaccessors `GetData` do pobierania danych automatycznie na wywołanie [MoveNext](../../data/oledb/crowset-movenext.md). Nonautomatic metody dostępu wymaga jawnie pobierania danych. Użyj nonautomatic dostępu są wiązane do pola dużej ilości danych (takich jak obraz mapy bitowej), którego nie można pobrać dla każdego rekordu.  
  
```  
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