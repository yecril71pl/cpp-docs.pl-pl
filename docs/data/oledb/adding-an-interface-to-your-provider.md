---
title: Dodawanie interfejsu do dostawcy
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: c0452ca74509b65de3787af93bff41b3cb399c99
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033877"
---
# <a name="adding-an-interface-to-your-provider"></a>Dodawanie interfejsu do dostawcy

Określić obiekt, do którego chcesz dodać interfejs do (zazwyczaj danych źródła, zestawu wierszy, polecenie lub sesji obiekty utworzone przez **OLE DB Provider kreatora**). Istnieje możliwość, że obiektu, należy dodać interfejs, który ma to taki, który Twój dostawca nie obsługuje obecnie. W takiej sytuacji Uruchom **Kreator biblioteki ATL OLE DB Provider** do utworzenia obiektu. Kliknij prawym przyciskiem myszy projekt w **Widok klas**, kliknij przycisk **Dodaj** > **nowy element** menu, wybierz polecenie **zainstalowane**  >  **Visual C++** > **ATL**, a następnie kliknij przycisk **dostawcy OLE DB ATL**. Warto umieścić kod interfejsu w oddzielnym katalogu, a następnie skopiuj pliki do projektu dostawcy.

Utworzono nową klasę do obsługi interfejsu, aby obiekt dziedziczą z klasy. Na przykład dodać klasę `IRowsetIndexImpl` do obiektu zestawu wierszy:

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

Dodawanie interfejsu do COM_MAP w obiekcie, użycie makra com_interface_entry —. Jeśli nie ma żadnych mapy, zrób to. Na przykład:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

Dla obiektu zestawu wierszy łańcuch mapy jego elementu nadrzędnego obiektu tak, aby delegować do klasy nadrzędnej obiektu. W tym przykładzie należy dodać makra COM_INTERFACE_ENTRY_CHAIN do mapy:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>Zobacz także

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)