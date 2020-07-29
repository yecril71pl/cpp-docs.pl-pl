---
title: Pionowa architektura widoku dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
ms.openlocfilehash: 8c7bb4add1ebce62147f0bd5403f693cbec87e91
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214194"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>Portret architektury dokument/widok

Dokumenty i widoki są sparowane w typowej aplikacji MFC. Dane są przechowywane w dokumencie, ale widok ma uprzywilejowany dostęp do danych. Rozdzielenie dokumentu z widoku oddziela magazyn i konserwację danych z jego wyświetlania.

## <a name="gaining-access-to-document-data-from-the-view"></a>Uzyskiwanie dostępu do danych dokumentu z widoku

Widok uzyskuje dostęp do danych dokumentu przy użyciu funkcji [GetDocument](reference/cview-class.md#getdocument) , która zwraca wskaźnik do dokumentu lub przez utworzenie klasy widoku w języku C++ **`friend`** klasy dokumentu. W widoku zostanie następnie użyty dostęp do danych w celu uzyskania danych, gdy wszystko jest gotowe do rysowania lub manipulowania nimi.

Na przykład, w funkcji składowej [OnDraw](reference/cview-class.md#ondraw) widoku, widok używa `GetDocument` do uzyskania wskaźnika dokumentu. Następnie używa tego wskaźnika, aby uzyskać dostęp do `CString` elementu członkowskiego danych w dokumencie. Widok przekazuje ciąg do `TextOut` funkcji. Aby wyświetlić kod dla tego przykładu, zobacz [Rysowanie w widoku](drawing-in-a-view.md).

## <a name="user-input-to-the-view"></a>Dane wejściowe użytkownika do widoku

Widok może również interpretować mysz w ramach zaznaczenia lub edycji danych. Podobnie można interpretować naciśnięcia klawiszy jako wprowadzania danych lub edytowania. Załóżmy, że użytkownik wpisze ciąg w widoku, który zarządza tekstem. Widok uzyskuje wskaźnik do dokumentu i używa wskaźnika, aby przekazać nowe dane do dokumentu, który przechowuje go w pewnej strukturze danych.

## <a name="updating-multiple-views-of-the-same-document"></a>Aktualizowanie wielu widoków tego samego dokumentu

W aplikacji z wieloma widokami tego samego dokumentu — na przykład okna rozdzielacza w edytorze tekstu — widok najpierw przekazuje nowe dane do dokumentu. Następnie wywołuje funkcję członkowską [funkcji UpdateAllViews](reference/cdocument-class.md#updateallviews) dokumentu, która informuje, że wszystkie widoki dokumentu zostaną zaktualizowane, odzwierciedlając nowe dane. Spowoduje to zsynchronizowanie widoków.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Zalety architektury dokument/widok](advantages-of-the-document-view-architecture.md)

- [Alternatywy dla architektury dokumentu/widoku](alternatives-to-the-document-view-architecture.md)

## <a name="see-also"></a>Zobacz także

[Architektura dokumentu/widoku](document-view-architecture.md)
