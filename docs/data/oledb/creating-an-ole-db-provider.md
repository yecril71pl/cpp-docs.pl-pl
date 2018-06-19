---
title: Tworzenie dostawcy OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f649b5b4c79c4148d0aed026b044485ca2b1eaa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097110"
---
# <a name="creating-an-ole-db-provider"></a>Tworzenie dostawcy OLE DB
Zalecanym sposobem tworzenia dostawcy OLE DB ma utworzyć Projekt ATL COM i dostawcy, a następnie zmodyfikować plików za pomocą szablonów OLE DB za pomocą kreatorów. Podczas dostosowywania dostawcy można przekształcić w komentarz zbędne właściwości i dodać opcjonalne interfejsów.  
  
 Podstawowe kroki są następujące:  
  
1.  Kreator projektu ATL do tworzenia plików projektu podstawowych i ATL OLE DB Provider kreatora, aby utworzyć dostawcę (wybierz **ATL dostawcy OLE DB** z folderu Visual C++ w **Dodaj klasę**).  
  
2.  Zmodyfikuj kod `Execute` w CMyProviderRS.h metody. Na przykład zobacz [odczytu ciągów do dostawcy OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).  
  
3.  Edytuj mapy właściwości w MyProviderDS.h, MyProviderSess.h i MyProviderRS.h. Kreator tworzy mapy właściwości, które zawierają wszystkie właściwości, które mogą zaimplementować dostawcę. Przejdź do mapy właściwości i usuń lub komentarz właściwości, które Twój dostawca nie obsługuje.  
  
4.  Zaktualizuj PROVIDER_COLUMN_MAP, który można znaleźć w MyProviderRS.h. Na przykład zobacz [przechowywanie ciągów w dostawcy OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).  
  
5.  Gdy wszystko będzie gotowe do testowania dostawcy, przetestować go przez próby znalezienia dostawcy w wyliczeniu dostawcy. Przykłady kodu, który umożliwia znalezienie dostawcę w wyliczeniu, zobacz [CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046) i [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) próbek lub przykład [Implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md).  
  
6.  Dodaj wszelkie dodatkowe interfejsy, które mają. Na przykład zobacz [udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
    > [!NOTE]
    >  Domyślnie kreatorów generuje kod, który jest OLE DB poziom 0 zgodne. Aby upewnić się, że aplikacja jest nadal poziom 0 zgodne, nie usuwaj żadnego z interfejsów generowanych przez kreatora z kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)