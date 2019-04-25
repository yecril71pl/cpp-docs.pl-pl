---
title: Operowanie listami obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: 1e86961980c91ade47a3d6510dec5c04ac36cffb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262791"
---
# <a name="manipulating-image-lists"></a>Operowanie listami obrazów

[Zastąp](../mfc/reference/cimagelist-class.md#replace) funkcji składowej zastępuje obraz w listy obrazów ([CImageList](../mfc/reference/cimagelist-class.md)) za pomocą nowego obrazu. Ta funkcja jest również przydatne, jeśli chcesz dynamicznie zwiększyć liczbę obrazów w obiekcie listy obrazów. [SetImageCount](../mfc/reference/cimagelist-class.md#setimagecount) funkcja dynamicznie zmienia Liczba obrazów przechowywanych w listy obrazów. Zwiększenie rozmiaru listy obrazów wywołać `Replace` dodać obrazy do nowego miejsca obrazu. Jeśli możesz zmniejszyć rozmiar listy obrazów, obrazy, poza nowy rozmiar są zwalniane.

[Usuń](../mfc/reference/cimagelist-class.md#remove) funkcja członkowska usuwa obraz z listy obrazów. [Kopiowania](../mfc/reference/cimagelist-class.md#copy) funkcja elementu członkowskiego można skopiować lub wymiany obrazy w obrębie listy obrazów. Tej funkcji można określić, czy obraz źródłowy powinien zostać skopiowany do indeksu docelowego, czy obraz źródłowy i docelowy powinien być zamienione.

Przez scalanie dwie listy obrazu, należy utworzyć nową listę obrazów, użyj odpowiedniej przeciążenia [Utwórz](../mfc/reference/cimagelist-class.md#create) funkcja elementu członkowskiego. To przeciążenie `Create` scalenia listy pierwsze obraz istniejącego obrazu, przechowywania obraz wynikowy w obiekcie listy obrazów. Nowy obraz jest tworzony za pomocą rysowania drugi obraz w sposób niewidoczny dla użytkownika za pośrednictwem pierwszego. Maska dla nowego obrazu jest wynikiem operacji logiczne OR na bity maski dla dwóch istniejących obrazów.

To jest powtarzany, dopóki wszystkie obrazy są scalane i dodawane do nowego obiektu listy obrazów.

Informacje o obrazie można zapisywać do archiwum, wywołując [zapisu](../mfc/reference/cimagelist-class.md#write) funkcja elementu członkowskiego, a także zapoznaj je z powrotem przez wywołanie metody [odczytu](../mfc/reference/cimagelist-class.md#read) funkcja elementu członkowskiego.

[GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle), [Attach](../mfc/reference/cimagelist-class.md#attach), i [Odłącz](../mfc/reference/cimagelist-class.md#detach) elementów członkowskich umożliwiają manipulowanie dojściem listy obrazów dołączonych do `CImageList` obiektu, gdy [DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist) funkcja członkowska usuwa listy obrazów bez niszczenia samego `CImageList` obiektu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
