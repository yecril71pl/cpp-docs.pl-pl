---
title: Zmiana czcionki tekstu obrazu (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a49cb4fa88b3a014d79969cc86fc03fa1136efa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405349"
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>Zmiana czcionki tekstu obrazu (Edytor obrazów dla ikon)

Poniższa procedura to przykład:

- Dodawanie tekstu do ikony w aplikacji Windows

- Manipulowanie czcionki tekstu

### <a name="to-change-the-font-of-text-on-an-image"></a>Zmiana czcionki tekstu obrazu

1. Tworzenie aplikacji formularzy Windows w języku C++. Aby uzyskać więcej informacji, zobacz [Tworzenie projektu aplikacji Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5\(v=vs.100\)). `app.ico` Plik zostanie dodany do projektu, domyślnie.

2. W **Eksploratora rozwiązań**, kliknij dwukrotnie app.ico pliku. [Edytora obrazów](../windows/image-editor-for-icons.md) zostanie otwarty.

3. Z **obraz** menu, wybierz opcję **narzędzia** , a następnie wybierz **narzędzie tekstowe**. [Okno dialogowe narzędzie tekstowe](../windows/text-tool-dialog-box-image-editor-for-icons.md) będą wyświetlane.

4. W **narzędzie tekstowe** okno dialogowe, typ `C++` w obszarze pusty tekst. Ten tekst będzie wyświetlany w polu o zmiennym rozmiarze, znajduje się w lewym górnym rogu `app.ico`w **edytora obrazów**.

5. W **edytora obrazów**, przeciągnij pole o zmiennych rozmiarach do środka app.ico można zwiększyć czytelność tekstu.

6. W **narzędzie tekstowe** okno dialogowe, kliknij przycisk **czcionki** przycisku. [Narzędzie czcionki tekstu, okno dialogowe](../windows/text-tool-font-dialog-box-image-editor-for-icons.md) będą wyświetlane.

7. W **narzędzie czcionki tekstu** okno dialogowe, wybierz opcję **podzbiory** z listy dostępnych czcionek, które są wymienione w **czcionki** pola listy.

8. Wybierz **Bold** z listy dostępnych style na liście **styl czcionki** pola listy.

9. Wybierz **10** z listy dostępnych punktów rozmiarów wymienionych w **rozmiar** pola listy.

10. Kliknij przycisk **OK** przycisku. **Narzędzie czcionki tekstu** okno dialogowe zostanie zamknięte i nowe ustawienia czcionek będą stosowane do tekstu.

11. Kliknij przycisk **Zamknij** znajdujący się na **narzędzie tekstowe** okno dialogowe. Pole o zmiennym rozmiarze wokół tekstu zniknie z **edytora obrazów**.

## <a name="see-also"></a>Zobacz też

[Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Pasek narzędzi](../windows/toolbar-image-editor-for-icons.md)