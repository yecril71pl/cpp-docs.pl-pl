---
title: Alokowanie zasobów GDI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae677a7d56eabba25de6124919eb226786174574
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427982"
---
# <a name="allocating-gdi-resources"></a>Alokowanie zasobów GDI

W tym artykule opisano sposób przydzielania i cofnąć jej przydział obiektów interface (GDI) urządzenia grafiki Windows niezbędnych do drukowania.

> [!NOTE]
>  Aby uzyskać więcej informacji, zobacz dokumentację zestawu SDK interfejsu GDI + w: [ https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp ](https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp).

Załóżmy, że należy użyć niektórych czcionek, pióra lub inne obiekty GDI związane z drukowaniem, ale nie do wyświetlania na ekranie. Ze względu na ilość pamięci, których potrzebują jest nieefektywne przydzielić tych obiektów, podczas uruchamiania aplikacji. Gdy aplikacja nie jest drukowanie dokumentu, że pamięć może być pożądane do innych celów. Zaleca się przydzielać je, po rozpoczęciu drukowania, a następnie usuń je, podczas drukowania kończy się.

Aby przydzielić te obiekty GDI, należy zastąpić [onbeginprinting —](../mfc/reference/cview-class.md#onbeginprinting) funkcja elementu członkowskiego. Ta funkcja jest dobrze nadaje się do tego celu dwóch powodów: struktura wywołuje tę funkcję, raz na początku każdego zadania drukowania i w przeciwieństwie do [onprepareprinting —](../mfc/reference/cview-class.md#onprepareprinting), funkcja ta ma dostęp do [CDC](../mfc/reference/cdc-class.md) Obiekt reprezentujący sterownika drukarki. Możesz przechowywać te obiekty do użycia podczas wykonywania zadania drukowania, definiując zmiennych składowych w klasie widoku wskazujące Obiekty GDI (na przykład `CFont *` składowych i tak dalej).

Aby użyć Obiekty GDI zostały utworzone, zaznacz je w kontekście urządzenia drukarki w [OnPrint](../mfc/reference/cview-class.md#onprint) funkcja elementu członkowskiego. Jeśli potrzebujesz różnych obiektów z użyciem interfejsu GDI dla różnych stron dokumentu, można sprawdzić `m_nCurPage` członkiem [cprintinfo —](../mfc/reference/cprintinfo-structure.md) struktury i w związku z tym wybierz obiekt GDI. Jeśli potrzebujesz obiektu interfejsu GDI dla kilku kolejnych stron Windows wymaga wybrania jej w kontekście urządzenia każdorazowo `OnPrint` jest wywoływana.

Aby cofnąć te obiekty GDI, Zastąp [onendprinting —](../mfc/reference/cview-class.md#onendprinting) funkcja elementu członkowskiego. Struktura wywołuje tę funkcję na końcu każdego zadania drukowania, co daje możliwość deallocate Obiekty GDI specyficzne dla drukowania, zanim aplikacja zwraca do innych zadań.

## <a name="see-also"></a>Zobacz też

[Drukowanie](../mfc/printing.md)<br/>
[Jak jest wykonywane drukowanie domyślne](../mfc/how-default-printing-is-done.md)

