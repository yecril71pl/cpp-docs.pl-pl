---
title: Dodawanie interfejsu do dostawcy
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: 295a7955b78918d6281a28b616f201869f37b01e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488676"
---
# <a name="adding-an-interface-to-your-provider"></a>Dodawanie interfejsu do dostawcy

Ustal, obiektu, który chcesz dodać interfejs do (zazwyczaj danych źródła, zestawu wierszy, polecenie lub sesji obiekty utworzone przez OLE DB Provider kreatora). Jest możliwe, że obiekt, należy dodać interfejs do jest taki, który nie obsługuje obecnie dostawcy. W takiej sytuacji Uruchom ATL OLE DB Provider kreatora, aby utworzyć obiekt. Kliknij prawym przyciskiem myszy projekt w widoku klas, kliknij przycisk **Dodaj klasę** z **Dodaj** menu, a następnie kliknij przycisk **ATL OLE DB Provider**. Warto umieścić kod interfejsu w oddzielnym katalogu, a następnie skopiuj pliki do projektu dostawcy.

Utworzono nową klasę do obsługi interfejsu, aby obiekt dziedziczą z klasy. Na przykład dodać klasę **IRowsetIndexImpl** do obiektu zestawu wierszy:

```cpp
template <class Creator>
class CAgentRowset :
    public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,
    public IRowsetIndexImpl< ... >
```

Dodawanie interfejsu do **COM_MAP** w obiekcie, użycie makra com_interface_entry —. Jeśli nie ma żadnych mapy, zrób to. Na przykład:

```cpp
BEGIN_COM_MAP(CAgentRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

Dla obiektu zestawu wierszy łańcuch mapy jego elementu nadrzędnego obiektu tak, aby delegować do klasy nadrzędnej obiektu. W tym przykładzie należy dodać makra COM_INTERFACE_ENTRY_CHAIN do mapy:

```cpp
BEGIN_COM_MAP(CAgentRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)