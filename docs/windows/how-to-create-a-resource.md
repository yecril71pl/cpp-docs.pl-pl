---
title: 'Instrukcje: Utwórz zasób (C++)'
ms.date: 11/04/2016
f1_keywords:
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- resources [C++], viewing
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
ms.openlocfilehash: fdf158bab7894497dbcfb147eb2c6e061879be75
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55764054"
---
# <a name="how-to-create-a-resource-c"></a>Instrukcje: Utwórz zasób (C++)

**Widok zasobów** okno wyświetla pliki zasobów zawarte w swoich projektach. Rozwijanie folderu najwyższego poziomu (na przykład Project1.rc) zawiera typy zasobów, w tym pliku .rc. Rozwijanie każdego typu zasobu zawiera poszczególne zasoby tego typu.

> [!NOTE]
> Te informacje nie ma zastosowania do zasobów w aplikacjach platformy uniwersalnej Windows. Aby uzyskać więcej informacji o tym, zobacz [zasobów aplikacji i systemu zarządzania zasobów](/windows/uwp/app-resources/).

> [!NOTE]
> **Widok zasobów** nie jest obsługiwana w wersji Express.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

**Widok zasobów** okno używa **Dodaj zasób** okno dialogowe, aby dodać zasoby do projektu aplikacji pulpitu Windows w języku C++. To okno dialogowe ma następujące właściwości:

|Właściwość|Opis|
|---|---|
|**Typ zasobu**|Określa rodzaj zasobu, który chcesz utworzyć.<br/><br/>Można rozwinąć kursora i okna dialogowego pole zasobów kategorie, aby ujawnić dodatkowe zasoby. Te zasoby znajdują się w programie Visual Studio ...\Microsoft `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Jeśli dodasz .rct — pliki, należy je umieścić w tym katalogu lub należy określić [ścieżki dołączania](../windows/how-to-specify-include-directories-for-resources.md) dla nich. Zasoby w tych plikach są następnie wyświetlane na drugim poziomie do odpowiedniej kategorii. Nie ma żadnych wstępnie limitu liczby .rct — pliki, które można dodać.<br/><br/>Zasoby pokazane na najwyższym poziomie w drzewie są domyślne zasoby, które są dostarczane przez program Visual Studio.|
|**Nowy**|Tworzy zasób, w zależności od typu wybranych w **typ zasobu** pole. Zasób zostanie otwarty w edytorze odpowiednie. Na przykład, jeśli tworzysz zasobu okna dialogowego, zostanie on otwarty w [Edytor okien dialogowych](../windows/dialog-editor.md).|
|**Importujuj**|Otwiera **zaimportować** okno dialogowe, w którym możesz przejść do zasobu należy czy mają zostać zaimportowane do bieżącego projektu. Możesz zaimportować mapy bitowej, ikony, kursor, plik zasobu HTML, dźwięk (. Plik zasobów WAV) lub plik zasobów niestandardowych.|
|**Custom**|Otwiera **nowy niestandardowy zasób** okno dialogowe, w którym można utworzyć zasobów niestandardowych. Zasoby niestandardowe można edytować w edytorze binarnym tylko.|

**Nowy niestandardowy zasób** okno dialogowe umożliwia utworzenie nowego zasobu niestandardowego w projekcie C++. To okno dialogowe ma następującą właściwość:

|Właściwość|Opis|
|---|---|
|**Typ zasobu**|Zawiera pole tekstowe do wprowadzenia nazwy typu zasobów niestandardowych. Visual C++ automatycznie powoduje rozpoczynanie nazwę podczas zamykania **nowy zasób niestandardowy** okno dialogowe.|

Podczas tworzenia nowego zasobu, Visual C++ przypisze unikatową nazwę, na przykład `IDD_Dialog1`. Tego Identyfikatora zasobu można dostosować, edytując właściwości zasobu w edytorze skojarzonego zasobu lub w [okno właściwości](/visualstudio/ide/reference/properties-window).

Można utworzyć zasobu jako nowego zasobu domyślnego (zasób, który nie jest oparty na szablonie) lub jako zasób deseniem po [szablonu](../windows/how-to-use-resource-templates.md).

> [!NOTE]
> Nie określaj nazwy zasobu lub identyfikator, który jest zarezerwowany przez program Visual Studio. Zarezerwowane nazwy to DESIGNINFO, HWB i TEXTINCLUDE, a zarezerwowany identyfikator to 255.

## <a name="to-open-the-resource-view-window"></a>Aby otworzyć okno Widok zasobów

Wybierz **widok zasobów** na **widoku** menu.

   \- lub —

Naciśnij klawisz **Ctrl** + **Shift** + **E**.

> [!TIP]
> Kliknięciu prawym przyciskiem myszy **widok zasobów** okna do uruchomienia poleceń menu skrótów. Możesz także dwukrotnie kliknąć na pasku tytułu, aby zadokować lub oddokować okno. Kliknij prawym przyciskiem myszy na pasku tytułu zapewni dodatkowe polecenia, które pozwalają na kontrolę zachowania okna. Aby uzyskać więcej informacji, zobacz [zarządzania Windows](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

## <a name="to-create-a-new-resource-in-resource-view"></a>Aby utworzyć nowy zasób w widoku zasobu

1. Fokus jest ustawiony w pliku .rc w **widok zasobów**, wybierz opcję **Edytuj** menu i wybierz polecenie **Dodaj zasób** (lub kliknij prawym przyciskiem myszy plik .rc w **widok zasobów** i wybierz polecenie **Dodaj zasób** z menu skrótów).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W **Dodaj zasób** okno dialogowe, wybierz typ zasobu, które chcesz dodać do projektu.

## <a name="to-create-a-new-resource-in-solution-explorer"></a>Aby utworzyć nowy zasób w Eksploratorze rozwiązań

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder projektu i wybierz polecenie **Dodaj**, następnie kliknij przycisk **Dodaj zasób** w menu skrótów.

   Jeśli nie masz jeszcze pliku .rc w projekcie, ten krok spowoduje utworzenie jednego. Następnie możesz powtórzyć ten krok, aby dodać określonych typów zasobów do nowego pliku .rc.

2. W **Dodaj zasób** okno dialogowe, wybierz typ zasobu, które chcesz dodać do projektu.

## <a name="to-create-a-new-resource-in-class-view"></a>Aby utworzyć nowy zasób w widoku klas

1. W [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy klasy i wybierz polecenie **Dodaj**, a następnie wybierz **Dodaj zasób** z menu skrótów.

2. W **Dodaj zasób** okno dialogowe, wybierz typ zasobu, które chcesz dodać do projektu.

## <a name="to-create-a-new-resource-from-the-project-menu"></a>Aby utworzyć nowy zasób z menu projektu

Z **projektu** menu, wybierz **Dodaj zasób**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)<br/>
