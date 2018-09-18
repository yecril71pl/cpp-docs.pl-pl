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
ms.openlocfilehash: f50459550c91f07c12f6f18b3fbbaa5622ab7408
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032396"
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