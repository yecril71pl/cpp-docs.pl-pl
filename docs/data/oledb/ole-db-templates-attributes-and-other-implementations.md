---
title: Szablony OLE DB, atrybuty oraz inne implementacje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7338f513754722bc00a96f5ee71cce06591f031d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685993"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>Szablony i atrybuty OLE DB oraz inne implementacje
## <a name="atl-ole-db-templates"></a>Szablony ATL OLE DB  
 Szablony OLE DB, które są częścią ATL (biblioteki Active Template Library), ułatwiają technologii baz danych OLE DB o wysokiej wydajności do użycia, zapewniając klas implementujących wiele powszechnie używanych interfejsów OLE DB. Wraz z tego szablonu biblioteka jest dostarczana Obsługa kreatora do tworzenia aplikacji starter OLE DB.  
  
 Ta biblioteka szablon zawiera dwie części:  
  
-   **Szablony OLE DB konsumenta** używaną do zaimplementowania aplikacja kliencka (użytkownik) OLE DB.  
  
-   **Szablony OLE DB Provider** używany do implementowania aplikacji serwera (dostawca) OLE DB.  
  
 Aby użyć szablonów OLE DB, należy zapoznać się z szablonów języka C++, COM i interfejsy OLE DB. Jeśli nie jesteś zaznajomiony z OLE DB, zobacz [OLE DB Podręcznik programisty](/previous-versions/windows/desktop/ms713643\(v=vs.85\)).  
  
 Aby uzyskać więcej informacji możesz wykonywać następujące czynności:  
  
-   Zapoznaj się z tematami o [szablony OLE DB konsumenta](../../data/oledb/ole-db-consumer-templates-cpp.md) lub [szablony OLE DB Provider](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
-   Tworzenie [konsumenta OLE DB](../../data/oledb/creating-an-ole-db-consumer.md) lub [dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md).  
  
-   Przejrzyj listę rzeczy, [klasy konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) lub [klasy dostawców OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).  
  
-   Przejrzyj listę rzeczy, [przykłady szablonów OLE DB](https://github.com/Microsoft/VCSamples).  
  
-   Zobacz [OLE DB Podręcznik programisty](/previous-versions/windows/desktop/ms713643\(v=vs.85\)) (w Windows SDK).  
  
## <a name="ole-db-attributes"></a>Atrybuty bazy danych OLE  
 [Atrybuty konsumentów OLE DB](../../windows/ole-db-consumer-attributes.md) zapewniają wygodny sposób, aby utworzyć konsumentów OLE DB. Atrybuty OLE DB wstrzyknięcie kodu, w oparciu o [szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) do utworzenia konsumentów OLE DB pracy i dostawców. Należy określić funkcji nieobsługiwanych przez atrybuty, można użyć szablonów OLE DB w połączeniu z atrybutów, w kodzie.  
  
## <a name="mfc-ole-db-classes"></a>Klasy MFC OLE DB  
 Biblioteka MFC zawiera jedną klasę [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), który wyświetla rekordy bazy danych w kontrolkach. Widok jest podłączone bezpośrednio do widoku formularza `CRowset` obiektu i wyświetla pola `CRowset` obiektu w kontrolkach szablonu okna dialogowego. Dostarcza również domyślna implementacja przechodzenia do pierwszego, dalej, poprzednie lub ostatni rekord a interfejsem aktualizowania rekordu aktualnie w widoku. Aby uzyskać więcej informacji, zobacz `COleDBRecordView`.  
  
## <a name="ole-db-sdk-interfaces"></a>OLE DB interfejsów zestawu SDK  
 W przypadkach, gdzie szablony OLE DB nie obsługują funkcji OLE DB należy użyć interfejsy OLE DB, samodzielnie. Aby uzyskać więcej informacji, zobacz [OLE DB Podręcznik programisty](/previous-versions/windows/desktop/ms713643\(v=vs.85\)) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie OLE DB](../../data/oledb/ole-db-programming.md)   
 [Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)