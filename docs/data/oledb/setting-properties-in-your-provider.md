---
title: Ustawianie właściwości w dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5d43e452d0fffcb4dc6eddcae722f8056dbd39dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109290"
---
# <a name="setting-properties-in-your-provider"></a>Ustawianie właściwości w dostawcy
Znajdź grupy właściwości i Identyfikatora właściwości dla właściwości, które mają. Aby uzyskać więcej informacji, zobacz [właściwości OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx) w *OLE DB Podręcznik programisty*.  
  
 W kodzie dostawcy generowane przez kreatora należy znaleźć mapę właściwości odpowiadającej właściwości grupy. Nazwa grupy właściwości zazwyczaj odpowiada zakresowi nazwę obiektu. Właściwości polecenia i zestawu wierszy znajdują się w poleceniu lub zestawu wierszy; właściwości źródła i Inicjowanie danych można znaleźć w obiekt źródła danych.  
  
 Mapy właściwości, należy dodać [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md) makra. PROPERTY_INFO_ENTRY_EX przyjmuje cztery parametry:  
  
-   Identyfikator właściwości odpowiadającej właściwości użytkownika. Najpierw siedmiu znaków ("DBPROP_") należy usunąć z przodu nazwę właściwości. Na przykład, jeśli chcesz dodać **DBPROP_MAXROWS**, Przekaż `MAXROWS` jako pierwszy element. Jeśli jest to właściwość niestandardową, należy przekazać Pełna nazwa identyfikatora GUID (na przykład `DBMYPROP_MYPROPERTY`).  
  
-   Typ wariantu właściwości (w [właściwości OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx) w *OLE DB Podręcznik programisty*). Wprowadź **VT_** typu (takich jak `VT_BOOL` lub `VT_I2`) odpowiednio do typu danych.  
  
-   Flagi, aby wskazać, czy właściwość jest do odczytu i zapisu oraz grupy, do którego należy. Na przykład następujący kod wskazuje właściwości odczytu/zapisu, należącego do grupy wierszy:  
  
    ```  
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE  
    ```  
  
-   Podstawową wartość właściwości. Może to być **wartość VARIANT_FALSE** wpisz wartość typu Boolean lub zero dla typu integer, na przykład. Właściwość ma tę wartość, o ile nie zostanie on zmieniony.  
  
    > [!NOTE]
    >  Niektóre właściwości są połączone lub powiązane łańcuchem zależności innych właściwości, takie jak zakładki lub aktualizacji. Jeśli konsumenta ustawia jedną właściwość na wartość true, mogą też skonfigurować ustawienie dla innej właściwości. Szablony dostawców OLE DB obsługuje to za pośrednictwem metody [CUtlProps::OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md).  
  
## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Właściwości ignorowane przez dostawców OLE DB firmy Microsoft  
 Dostawcy OLE DB firmy Microsoft Ignoruj następujące właściwości OLE DB:  
  
-   **DBPROP_MAXROWS** działa tylko dla dostawcy tylko do odczytu (oznacza to, gdzie DBPROP_IRowsetChange i DBPROP_IRowsetUpdate są false); w przeciwnym razie ta właściwość nie jest obsługiwana.  
  
-   **DBPROP_MAXPENDINGROWS** jest zignorowana; dostawcy określa własnej limit.  
  
-   **DBPROP_MAXOPENROWS** jest zignorowana; dostawcy określa własnej limit.  
  
-   **DBPROP_CANHOLDROWS** jest zignorowana; dostawcy określa własnej limit.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)