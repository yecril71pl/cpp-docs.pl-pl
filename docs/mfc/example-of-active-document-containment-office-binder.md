---
title: 'Przykład zawierania dokumentów aktywnych: Office Binder'
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
ms.openlocfilehash: fe9ccb5b78d9a60c5b8b2a19fe0818a8e1682f00
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623122"
---
# <a name="example-of-active-document-containment-office-binder"></a>Przykład zawierania dokumentów aktywnych: Office Binder

Microsoft Office spinaczem jest przykładem aktywnego kontenera dokumentów. Program Office Binder zawiera dwa podstawowe okienka, jak zwykle kontenery. Okienko po lewej stronie zawiera ikony, które odpowiadają aktywnym dokumentom w spinaczu. Każdy dokument jest nazywany *sekcją* w spinaczu. Na przykład spinacz może zawierać dokumenty programu Word, pliki programu PowerPoint, arkusze kalkulacyjne programu Excel itd.

Kliknięcie ikony w lewym okienku aktywuje odpowiadający jej aktywny dokument. W prawym okienku spinacza zostanie wyświetlona zawartość aktualnie wybranego aktywnego dokumentu.

W przypadku otwarcia i aktywowania dokumentu programu Word w spinaczu pasek menu programu Word i paski narzędzi są wyświetlane w górnej części ramki widoku i można edytować zawartość dokumentu przy użyciu dowolnego polecenia programu Word lub narzędzia. Jednak pasek menu jest kombinacją pasków menu spinacza i programu Word. Ponieważ zarówno spinacz, jak i Word mają menu **Pomoc** , zawartość odpowiednich menu jest scalana. Kontenery dokumentów aktywnych, takie jak Office Binder, automatycznie udostępniają scalanie menu **Pomoc** . Aby uzyskać więcej informacji, zobacz [scalanie menu Pomoc](help-menu-merging.md).

Po wybraniu aktywnego dokumentu innego typu aplikacji, interfejs spinacza zmienia się w celu uwzględnienia tego typu aplikacji aktywnego dokumentu. Na przykład, jeśli spinacz zawiera arkusz kalkulacyjny programu Excel, zobaczysz, że menu w spinaczu zmienią się po zaznaczeniu sekcji arkusza kalkulacyjnego programu Excel.

Istnieją oczywiście inne możliwe typy kontenerów obok powiązań. Eksplorator plików używa typowego interfejsu dwuokienkowego, w którym lewe okienko używa kontrolki drzewa do wyświetlania hierarchicznej listy katalogów w stacji lub sieci, podczas gdy w okienku po prawej stronie są wyświetlane pliki zawarte w aktualnie wybranym katalogu. Przeglądarka internetowa — typ kontenera (na przykład Microsoft Internet Explorer), a nie za pomocą interfejsu dwuokienkowego, zazwyczaj ma jedną ramkę i udostępnia nawigację przy użyciu hiperłączy.

## <a name="see-also"></a>Zobacz też

[Zawieranie dokumentów aktywnych](active-document-containment.md)
