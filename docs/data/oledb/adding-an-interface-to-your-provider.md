---
title: Dodawanie interfejsu do dostawcy
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: b13d1224388dc7d3218dea1c70b5aa8a595fcbdb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212334"
---
# <a name="adding-an-interface-to-your-provider"></a>Dodawanie interfejsu do dostawcy

> [!NOTE]
> Kreator dostawcy OLE DB ATL nie jest dostępny w programie Visual Studio 2019 i nowszych.

Określ, który obiekt ma zostać dodany do interfejsu (zazwyczaj źródła danych, zestawu wierszy, polecenia lub obiektów sesji utworzonych przez **Kreatora dostawcy OLE DB**). Istnieje możliwość, że obiekt, do którego należy dodać interfejs, jest taki, który nie jest obecnie obsługiwany przez dostawcę. W takim przypadku uruchom **kreatora ATL OLE DB Provider** , aby utworzyć obiekt. Kliknij prawym przyciskiem myszy projekt w **Widok klasy**, kliknij polecenie **Dodaj** > **nowy element** z menu, wybierz pozycję **zainstalowane** > **Visual C++**  > **ATL**, a następnie kliknij pozycję **dostawca OLEDB OLE**. Możesz chcieć umieścić kod interfejsu w osobnym katalogu, a następnie skopiować pliki do projektu dostawcy.

Jeśli utworzono nową klasę do obsługi interfejsu, ustaw obiekt jako Dziedziczony z tej klasy. Na przykład można dodać klasę `IRowsetIndexImpl` do obiektu zestawu wierszy:

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

Dodaj interfejs do COM_MAP w obiekcie przy użyciu makra COM_INTERFACE_ENTRY. Jeśli nie ma mapy, utwórz ją. Na przykład:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

Dla obiektu zestawu wierszy należy utworzyć łańcuch mapowania jego obiektu nadrzędnego, aby obiekt mógł delegować do klasy nadrzędnej. W tym przykładzie Dodaj makro COM_INTERFACE_ENTRY_CHAIN do mapy:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
