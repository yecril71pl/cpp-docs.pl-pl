---
title: Operowanie listami obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: cb7376241febd6bd1545cd183147e14a15313820
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622461"
---
# <a name="manipulating-image-lists"></a>Operowanie listami obrazów

Funkcja [replace](reference/cimagelist-class.md#replace) member zamienia obraz na liście obrazów ([Korzystanie CImageList](reference/cimagelist-class.md)) na nowy obraz. Ta funkcja jest również przydatna, jeśli konieczne jest dynamiczne zwiększenie liczby obrazów w obiekcie listy obrazów. Funkcja [SetImageCount](reference/cimagelist-class.md#setimagecount) dynamicznie zmienia liczbę obrazów przechowywanych na liście obrazów. W przypadku zwiększenia rozmiaru listy obrazów należy wywołać `Replace` Dodawanie obrazów do nowych miejsc obrazu. Zmniejszenie rozmiaru listy obrazów pozwala zwolnić obrazy poza nowym rozmiarem.

Funkcja [usuwania](reference/cimagelist-class.md#remove) elementu członkowskiego usuwa obraz z listy obrazów. Funkcja [kopiowania](reference/cimagelist-class.md#copy) elementów członkowskich może kopiować lub zamieniać obrazy na liście obrazów. Ta funkcja pozwala wskazać, czy obraz źródłowy ma być kopiowany do indeksu docelowego, czy obrazy źródłowe i docelowe powinny zostać zamienione.

Aby utworzyć nową listę obrazów przez scalenie dwóch list obrazów, użyj odpowiedniego przeciążenia funkcji [tworzenia](reference/cimagelist-class.md#create) elementu członkowskiego. To przeciążenie polega na `Create` scaleniu pierwszego obrazu istniejących list obrazów, przechowując wynikowy obraz w nowym obiekcie listy obrazów. Nowy obraz jest tworzony przez rysowanie drugiego obrazu w sposób niewidoczny w pierwszej kolejności. Maska dla nowego obrazu jest wynikiem wykonywania logicznej operacji na bitach masek dla obu istniejących obrazów.

Jest to powtarzane, dopóki wszystkie obrazy nie zostaną scalone i dodane do nowego obiektu listy obrazów.

Informacje o obrazie można zapisać do archiwum, wywołując funkcję składowej [zapisu](reference/cimagelist-class.md#write) i odczytając ją ponownie przez wywołanie funkcji [odczytu](reference/cimagelist-class.md#read) elementu członkowskiego.

Funkcje [GetSafeHandle](reference/cimagelist-class.md#getsafehandle), [Attach](reference/cimagelist-class.md#attach)i [Odłącz](reference/cimagelist-class.md#detach) składowe umożliwiają manipulowanie uchwytem listy obrazów dołączonej do `CImageList` obiektu, natomiast funkcja członkowska [DeleteImageList](reference/cimagelist-class.md#deleteimagelist) usuwa listę obrazów bez niszczenia `CImageList` obiektu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CImageList](using-cimagelist.md)<br/>
[Formanty](controls-mfc.md)
