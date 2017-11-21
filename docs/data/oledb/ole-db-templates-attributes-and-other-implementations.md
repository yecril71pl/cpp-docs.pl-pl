---
title: Szablony OLE DB, atrybuty oraz inne implementacje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0dc00e20d1177de7532e0da121874476ad9fde2a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>Szablony i atrybuty OLE DB oraz inne implementacje
## <a name="atl-ole-db-templates"></a>Szablony ATL OLE DB  
 Szablony OLE DB, które są częścią ATL (biblioteki Active Template Library), ułatwiają z technologii bazy danych OLE DB wysokiej wydajności wpisując klas implementujących wiele często używane interfejsy OLE DB. Wraz z tego szablonu biblioteka jest dostarczana obsługę Kreatora tworzenia aplikacji starter OLE DB.  
  
 Ta biblioteka szablonów zawiera dwa składniki:  
  
-   **Szablony OLE DB konsumenta** używaną do zaimplementowania w aplikacji OLE DB klienta (użytkownika).  
  
-   **Szablony OLE DB Provider** używaną do zaimplementowania OLE DB aplikacji serwera (dostawcy).  
  
 Aby użyć szablonów OLE DB, należy zapoznać się z szablonów języka C++, COM i interfejsy OLE DB. Jeśli nie masz doświadczenia z OLE DB, zobacz [OLE DB Podręcznik programisty](https://msdn.microsoft.com/en-us/library/ms713643.aspx).  
  
 Aby uzyskać więcej informacji można:  
  
-   Przeczytaj tematy dotyczące [szablony OLE DB konsumenta](../../data/oledb/ole-db-consumer-templates-cpp.md) lub [szablony OLE DB Provider](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
-   Utwórz [konsumenta OLE DB](../../data/oledb/creating-an-ole-db-consumer.md) lub [dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md).  
  
-   Lista [klasy konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) lub [klasy dostawców OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).  
  
-   Lista [przykłady szablonów OLE DB](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c).  
  
-   Zobacz [OLE DB Podręcznik programisty](https://msdn.microsoft.com/en-us/library/ms713643.aspx) (w systemie Windows SDK).  
  
## <a name="ole-db-attributes"></a>Atrybuty bazy danych OLE  
 [Atrybuty konsumentów OLE DB](../../windows/ole-db-consumer-attributes.md) zapewnić wygodny sposób utworzyć konsumentów OLE DB. Atrybuty OLE DB wstrzyknięcie kodu na podstawie [szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) można utworzyć pracy konsumentów OLE DB i dostawców. Jeśli trzeba określić funkcje nieobsługiwane przez atrybuty, można użyć szablonów OLE DB w połączeniu z atrybutami w kodzie.  
  
## <a name="mfc-ole-db-classes"></a>Klasy MFC OLE DB  
 Biblioteka MFC ma jedną klasę [coledbrecordview —](../../mfc/reference/coledbrecordview-class.md), który wyświetla w formantach rekordów bazy danych. Widok jest widokiem formularza bezpośrednio podłączone do `CRowset` obiektu i są wyświetlane pola `CRowset` obiektu w formantach szablonu okna dialogowego. Domyślna implementacja przenoszenia zawiera także jako pierwszy dalej, poprzedniego lub ostatniego rekordu i interfejs aktualizowania rekordu w widoku. Aby uzyskać więcej informacji, zobacz `COleDBRecordView`.  
  
## <a name="ole-db-sdk-interfaces"></a>OLE DB interfejsów zestawu SDK  
 W przypadkach, gdy szablony OLE DB nie obsługują funkcji OLE DB musisz użyć same interfejsy OLE DB. Aby uzyskać więcej informacji, zobacz [OLE DB Podręcznik programisty](https://msdn.microsoft.com/en-us/library/ms713643.aspx) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie OLE DB](../../data/oledb/ole-db-programming.md)   
 [Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)