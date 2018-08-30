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
ms.openlocfilehash: 16d78d590201ea637dd6153edb40a1c6d89a82c0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210344"
---
# <a name="creating-an-ole-db-provider"></a>Tworzenie dostawcy OLE DB
Zalecany sposób tworzenia dostawcy OLE DB jest za pomocą kreatorów, aby utworzyć Projekt ATL COM i dostawcy, a następnie zmodyfikuj pliki przy użyciu szablonów OLE DB. Podczas dostosowywania dostawcy można przekształcić w komentarz zbędne właściwości i dodać opcjonalne interfejsy.  
  
 Podstawowe kroki są następujące:  
  
1.  Tworzenie plików podstawowego projektu i ATL OLE DB Provider kreatora, aby utworzyć dostawcę za pomocą Kreatora projektu ATL (wybierz **ATL OLE DB Provider** z folderu Visual C++ w **Dodaj klasę**).  
  
2.  Zmodyfikuj kod `Execute` metody w CMyProviderRS.h. Aby uzyskać przykład, zobacz [odczyt ciągów do dostawcy OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).  
  
3.  Edytuj mapy właściwości w MyProviderDS.h, MyProviderSess.h i MyProviderRS.h. Kreator utworzy map właściwości, które zawierają wszystkie właściwości, które mogą zaimplementować dostawcę. Przejdź do mapy właściwości i usuń lub komentarz właściwości, które Twój dostawca musi obsługiwać.  
  
4.  Zaktualizuj PROVIDER_COLUMN_MAP, który można znaleźć w MyProviderRS.h. Aby uzyskać przykład, zobacz [przechowywanie ciągów w dostawcy OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).  
  
5.  Gdy wszystko jest gotowe do testowania dostawcy, można ją przetestować, próbując znaleźć dostawcy w wyliczeniu dostawcy. Aby zapoznać się z przykładami kodu, który umożliwia znalezienie dostawcy w wyliczeniu, zobacz [CATDB](https://github.com/Microsoft/VCSamples) i [DBVIEWER](https://github.com/Microsoft/VCSamples) próbek lub w przykładzie w [Implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md).  
  
6.  Dodaj wszelkie dodatkowe interfejsy, które chcesz. Aby uzyskać przykład, zobacz [udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
    > [!NOTE]
    >  Domyślnie kreatorów wygenerować kod, który jest poziom OLE DB 0 zgodne. Aby upewnić się, że aplikacja pozostanie poziom 0 jest zgodne, nie usuwaj żadnego z interfejsów generowane przez kreatora z kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [CATDB](https://github.com/Microsoft/VCSamples)   
 [DBVIEWER](https://github.com/Microsoft/VCSamples)