---
title: Rekordy użytkownika
ms.date: 05/09/2019
f1_keywords:
- COLUMN_ENTRY_MAP
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
ms.openlocfilehash: 2de4cc9227da9d4ad8a012dacd85500ab698c4ae
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509435"
---
# <a name="user-records"></a>Rekordy użytkownika

> [!NOTE]
> Kreator użytkownika ATL OLE DB nie jest dostępny w programie Visual Studio 2019 i nowszych. Można nadal ręcznie dodawać funkcje. Aby uzyskać więcej informacji, zobacz [Tworzenie klienta bez korzystania z Kreatora](creating-a-consumer-without-using-a-wizard.md).

Aby użyć statycznej metody dostępu (czyli metody dostępu pochodnej od `CAccessor` ), odbiorca musi mieć rekord użytkownika. Rekord użytkownika jest klasą języka C++, która zawiera elementy danych do obsługi danych wejściowych lub wyjściowych. **Kreator OLE DB klienta ATL** generuje rekord użytkownika dla konsumenta. Do rekordu użytkownika można dodać metody dla opcjonalnych zadań, takich jak obsługa poleceń.

Poniższy kod przedstawia przykładowy rekord, który obsługuje polecenia. W rekordzie użytkownika BEGIN_COLUMN_MAP reprezentuje zestaw wierszy danych przesłany do konsumenta od dostawcy. BEGIN_PARAM_MAP reprezentuje zestaw parametrów poleceń. W tym przykładzie zastosowano klasę [CCommand](../../data/oledb/ccommand-class.md) , aby obsłużyć parametry polecenia. Elementy członkowskie danych w pozycji mapy reprezentują przesunięcia do jednego ciągłego bloku pamięci dla każdego wystąpienia klasy. Makra COLUMN_ENTRY odpowiadają makro PROVIDER_COLUMN_ENTRY po stronie dostawcy.

Aby uzyskać więcej informacji na temat COLUMN_MAP i PARAM_MAP makr, zobacz [MACROS for OLE DB templates](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

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

## <a name="wizard-generated-user-records"></a>Rekordy użytkowników generowane przez Kreatora

Jeśli użytkownik korzysta z **kreatora ATL OLE DB Consumer** do wygenerowania konsumenta, będziesz mieć możliwość użycia szablonów OLE DB lub atrybutów OLE DB. Wygenerowany kod jest różny w każdym przypadku. Aby uzyskać więcej informacji na temat tego kodu, zobacz [klasy klienta generowane przez kreatora](../../data/oledb/consumer-wizard-generated-classes.md).

## <a name="user-record-support-for-multiple-accessors"></a>Obsługa rekordów użytkowników dla wielu metod dostępu

Aby uzyskać szczegółowe omówienie scenariuszy, w których należy użyć wielu metod dostępu, zobacz [Używanie wielu metod dostępu w zestawie wierszy](../../data/oledb/using-multiple-accessors-on-a-rowset.md).

Poniższy przykład pokazuje rekord użytkownika zmodyfikowany w celu obsługi wielu metod dostępu w zestawie wierszy. Zamiast BEGIN_COLUMN_MAP i END_COLUMN_MAP, używa [BEGIN_ACCESSOR_MAP](./macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor_map) i [BEGIN_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor) dla każdego metody dostępu. Makro BEGIN_ACCESSOR określa numer akcesora (przesunięcie od zera) i czy akcesor jest autodostępnym. Autodostępy są wywoływane `GetData` w celu automatycznego pobierania danych w wywołaniu elementu [MoveNext](./crowset-class.md#movenext). Nieautomatyczne metody dostępu wymagają jawnego pobrania danych. Użyj nieautomatycznej metody dostępu, jeśli łączysz się z dużym polem danych (na przykład obrazem mapy bitowej), które może nie być pobierane dla każdego rekordu.

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

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)
