---
title: 'Instrukcje: Kopiowanie zasobów (C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 772c9b905d4cb0c4e2ccab9ec51aa02860b2db32
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849664"
---
# <a name="how-to-copy-resources-c"></a>Instrukcje: Kopiowanie zasobów (C++)

Możesz skopiować zasoby z jednego pliku do innego bez ich zmieniania lub zmienić języka lub warunku zasobu podczas kopiowania go.

Można go łatwo skopiować zasoby z istniejącego zasobu lub plik wykonywalny do bieżącego pliku zasobów. Aby umożliwić kopiowanie zasobów, możesz otworzyć oba pliki zawierające zasoby w tym samym czasie i przeciągnij elementy z jednego pliku lub skopiuj i Wklej między dwoma plikami. Ta metoda działa dla plików skryptu (.rc) zasobów i plików szablonów (.rct) zasobu, a także jako pliki wykonywalne (.exe).

> [!NOTE]
> Visual C++ zawiera przykładowe pliki zasobów, które można użyć w swojej aplikacji. Aby uzyskać więcej informacji, zobacz [CLIPART: Wspólnych zasobów](https://github.com/Microsoft/VCSamples).

Metodą przeciągania i upuszczania między plikami .rc, które są otwarte [poza projektem](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

## <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Aby umożliwić kopiowanie zasobów między plikami przy użyciu metody przeciągania i upuszczania

1. Otwórz zarówno autonomiczne pliki zasobów (Aby uzyskać więcej informacji, zobacz [wyświetlanie zasobów .rc z zewnętrznego pliku projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Na przykład otworzyć Source1.rc i Source2.rc.

1. W pierwszym pliku .rc wybierz zasób, który chcesz skopiować. Na przykład w `Source1.rc`, wybierz opcję **IDD_DIALOG1**.

1. Naciśnij i przytrzymaj **Ctrl** klucza i przeciągnij go do drugiego pliku .rc. Na przykład przeciągać **IDD_DIALOG1** z `Source1.rc` do `Source2.rc`.

   > [!NOTE]
   > Przeciąganie zasób bez przytrzymywania **Ctrl** klucz przenosi zasobu, a nie skopiować go.

## <a name="to-copy-resources-using-copy-and-paste"></a>Do kopiowania zasobów za pomocą kopiowania i wklejania

1. Otwórz zarówno autonomiczne pliki zasobów (Aby uzyskać więcej informacji, zobacz [wyświetlanie zasobów .rc z zewnętrznego pliku projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Na przykład Source1.rc i Source2.rc.

1. W pliku źródłowym, z którego chcesz skopiować zasobu (na przykład `Source1.rc`), kliknij prawym przyciskiem myszy zasób i wybierz polecenie **kopiowania** z menu skrótów.

1. Kliknij prawym przyciskiem myszy plik zasobów, do którego chcesz wkleić zasobu (na przykład `Source2.rc`). Wybierz **Wklej** z menu skrótów.

   > [!NOTE]
   > Użytkownik nie przeciągnij i upuść, kopiowanie, wycinanie lub wklejanie danych między plikami zasobów w projekcie (**widok zasobów**) i pliki .rc autonomicznej, (te otwarte w oknach dokumentów). Można to zrobić w poprzednich wersjach produktu.

   > [!NOTE]
   > Aby uniknąć konfliktów z nazwami symboli lub wartości z istniejącego pliku, Visual C++ może ulec zmianie wartości symboli zasobu przeniesionych lub nazwy symbolu i wartości po skopiuj go do nowego pliku.

## <a name="to-change-the-language-or-condition-of-a-resource-while-copying-c"></a>Aby zmiana języka lub warunku zasobu podczas kopiowania (C++)

Podczas kopiowania w zasobach, można zmienić jego właściwość języka i/lub właściwości warunku.

- Język zasobu identyfikuje taką, języka zasobu. Język jest używany przez [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) ułatwia zidentyfikowanie zasobów, dla których potrzebujesz. (Jednak zasoby mogą znajdować się różnic dla każdego z języków, które nie są związane z tekstu, na przykład tworzy akceleratorów, które może działać wyłącznie względem klawiatury japońskiej lub mapy bitowej, która byłaby tylko odpowiednie dla zlokalizowanego języka chińskiego)

- Stan zasobu jest zdefiniowany symbol, który określa warunek, w ramach której ma zostać użyty określonej kopii zasobu.

Język i warunku zasobu są wyświetlane w nawiasach, po nazwie zasobu w okno obszaru roboczego. W tym przykładzie zasobu o nazwie IDD_AboutBox używa fiński jako język, a jego stan jest XX33.

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Aby skopiować istniejący zasób i zmień jego języka lub warunku

1. W pliku .rc, lub w [widok zasobów](../windows/resource-view-window.md) okna, kliknij prawym przyciskiem myszy zasób, którego chcesz skopiować.

1. Wybierz **Wstaw kopiowania** z menu skrótów.

1. W **Wstaw kopię zasobu** okno dialogowe:

   - Aby uzyskać **języka** pola listy, wybierz język.

   - W **warunek** wpisz warunek.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)<br/>
[Instrukcje: otwieranie pliku skryptu zasobu spoza projektu (autonomicznego)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
