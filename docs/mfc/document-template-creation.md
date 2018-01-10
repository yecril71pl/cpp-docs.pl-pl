---
title: Tworzenie szablonu dokumentu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 04950601a74b1ed3e44b236e1d07dcdff997eca6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="document-template-creation"></a>Tworzenie szablonu dokumentu
Podczas tworzenia nowego dokumentu w odpowiedzi na `New` lub **Otwórz** polecenie **pliku** menu szablonu dokumentu również tworzy nowe okno ramowe za pośrednictwem której można wyświetlić dokument.  
  
 Konstruktor szablonu dokumentu określa, jakie typy dokumentów, okien i widoków szablonu będą mogli tworzyć. Jest to określane przez argumenty, które można przekazać do konstruktora szablonu dokumentu. Poniższy kod przedstawia tworzenie [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) przykładową aplikację:  
  
 [!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]  
  
 Wskaźnik do nowego `CMultiDocTemplate` obiekt jest używany jako argument [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate). Argumenty `CMultiDocTemplate` Konstruktor zawierać identyfikator zasobu skojarzone z menu i akceleratorami typu dokumentu i trzy stosowania [runtime_class —](../mfc/reference/run-time-object-model-services.md#runtime_class) makra. `RUNTIME_CLASS`Zwraca [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) obiektu klasy C++ o nazwie jako jej argument. Trzy `CRuntimeClass` obiektów przekazany do konstruktora szablonu dokumentu, podaj informacje potrzebne do tworzenia nowych obiektów klasy określonej w trakcie procesu tworzenia dokumentu. W przykładzie pokazano tworzenie szablonu dokumentu, który tworzy `CScribDoc` obiekty z `CScribView` obiektów dołączonych. Widoki są w ramce przez standardowe okien ramowych podrzędnych MDI.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)   
 [Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)   
 [Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)

