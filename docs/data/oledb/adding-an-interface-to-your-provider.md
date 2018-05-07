---
title: Dodawanie interfejsu do dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3d6bc5d1b6c47d2ffa26bffa98d47b930d6ed193
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="adding-an-interface-to-your-provider"></a>Dodawanie interfejsu do dostawcy
Określenia, które obiekty chcesz dodać interfejsu (zazwyczaj danych źródła wierszy, polecenie albo sesji obiektów utworzonych przez kreatora dostawcy bazy danych OLE). Istnieje możliwość, że obiekt, należy dodać interfejs do to taki, który dostawca nie obsługuje obecnie. W takim przypadku Kreator ATL OLE DB dostawcy do utworzenia obiektu. Kliknij prawym przyciskiem myszy projekt w widoku klas, kliknij przycisk **Dodaj klasę** z **Dodaj** menu, a następnie kliknij przycisk **ATL dostawcy OLE DB**. Możesz chcieć umieść kod interfejsu w oddzielnym katalogu, a następnie skopiuj pliki do projektu dostawcy.  
  
 Jeśli utworzono nową klasę do obsługi interfejsu, powoduje, że obiekt dziedziczyć po tej klasie. Na przykład można dodać klasy **IRowsetIndexImpl** do obiektu zestawu wierszy:  
  
```cpp  
template <class Creator>  
class CAgentRowset :   
    public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,  
    public IRowsetIndexImpl< ... >   
```  
  
 Dodawanie interfejsu do **COM_MAP** w obiekcie użycie makra com_interface_entry —. Jeśli nie ma żadnych mapy, utwórz je. Na przykład:  
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
END_COM_MAP()  
```  
  
 Dla obiektu zestawu wierszy łańcuch mapy jego elementu nadrzędnego obiektu tak, aby obiekt można delegować do klasy nadrzędnej. W tym przykładzie należy dodać makra COM_INTERFACE_ENTRY_CHAIN do mapy:  
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)  
END_COM_MAP()  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)