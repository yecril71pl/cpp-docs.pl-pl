---
title: Tworzenie szablonu dokumentów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b1a9067929e96c6d3fd851168af079e7e825dcb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443636"
---
# <a name="document-template-creation"></a>Tworzenie szablonu dokumentu

Podczas tworzenia nowego dokumentu w odpowiedzi na **New** lub **Otwórz** polecenia **pliku** menu Szablon dokumentu, który również tworzy nowe okno ramki za pomocą którego można wyświetlić dokument.

Konstruktor szablonu dokumentu określa, jakie typy dokumentów, okien i widoków, które szablon będzie można utworzyć. Jest to określane przez argumenty przekazywane do konstruktora szablonu dokumentu. Poniższy kod ilustruje tworzenie [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) przykładowej aplikacji:

[!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]

Wskaźnik do nowego `CMultiDocTemplate` obiekt jest używany jako argument do [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate). Argumenty `CMultiDocTemplate` Konstruktor obejmują identyfikator zasobu skojarzony z typem dokumentu menu i akceleratorami i używa trzech z [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) makra. `RUNTIME_CLASS` Zwraca [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) obiektu dla klasy języka C++ o nazwie jako argumentem. Trzy `CRuntimeClass` obiektów przekazany do konstruktora szablonu dokumentu, podaj informacje potrzebne do utworzenia nowych obiektów określonych klas w trakcie procesu tworzenia dokumentu. W przykładzie pokazano tworzenie szablonu dokumentu, który tworzy `CScribDoc` obiekty z `CScribView` obiektów dołączonych. Widoki jest otoczony standardowa okien ramek podrzędnych MDI.

## <a name="see-also"></a>Zobacz też

[Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)<br/>
[Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)

