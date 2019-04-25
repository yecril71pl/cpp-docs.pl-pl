---
title: Tworzenie szablonu dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
ms.openlocfilehash: 85ff6ad47b37d85c812608dbee918f0543730eae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219811"
---
# <a name="document-template-creation"></a>Tworzenie szablonu dokumentu

Podczas tworzenia nowego dokumentu w odpowiedzi na **New** lub **Otwórz** polecenia **pliku** menu Szablon dokumentu, który również tworzy nowe okno ramki za pomocą którego można wyświetlić dokument.

Konstruktor szablonu dokumentu określa, jakie typy dokumentów, okien i widoków, które szablon będzie można utworzyć. Jest to określane przez argumenty przekazywane do konstruktora szablonu dokumentu. Poniższy kod ilustruje tworzenie [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) przykładowej aplikacji:

[!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]

Wskaźnik do nowego `CMultiDocTemplate` obiekt jest używany jako argument do [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate). Argumenty `CMultiDocTemplate` Konstruktor obejmują identyfikator zasobu skojarzony z typem dokumentu menu i akceleratorami i używa trzech z [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) makra. `RUNTIME_CLASS` Zwraca [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) obiektu dla klasy języka C++ o nazwie jako argumentem. Trzy `CRuntimeClass` obiektów przekazany do konstruktora szablonu dokumentu, podaj informacje potrzebne do utworzenia nowych obiektów określonych klas w trakcie procesu tworzenia dokumentu. W przykładzie pokazano tworzenie szablonu dokumentu, który tworzy `CScribDoc` obiekty z `CScribView` obiektów dołączonych. Widoki jest otoczony standardowa okien ramek podrzędnych MDI.

## <a name="see-also"></a>Zobacz także

[Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)<br/>
[Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)
