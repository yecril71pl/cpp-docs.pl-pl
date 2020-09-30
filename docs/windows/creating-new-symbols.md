---
title: 'Instrukcje: Tworzenie symboli (C++)'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.creating
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
- vc.editors.symbol.resource
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
- resource symbols
- View Use button
- resource editors [C++], resource symbols
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
ms.openlocfilehash: 008d2ab420034e628251c08222bf2e9f723deab1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504500"
---
# <a name="how-to-create-symbols-c"></a>Instrukcje: Tworzenie symboli (C++)

Gdy rozpoczynasz nowy projekt, może być przydatne zamapowanie nazw symboli przed utworzeniem zasobów, do których zostaną przypisane.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku. RC, zobacz [How to: Create Resources](../windows/how-to-create-a-resource-script-file.md).

W oknie dialogowym **symbole zasobów** można dodawać nowe symbole zasobów, zmieniać wyświetlane symbole lub przeskoczyć do lokalizacji w kodzie źródłowym, w którym jest używany symbol.

Okno dialogowe zawiera następujące właściwości:

|Właściwość|Opis|
|--------------------------|------------------------------------------|
|**Nazwa**|Wyświetla nazwę symbolu.<br/><br/>Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące nazw symboli](./changing-a-symbol-or-symbol-name-id.md).|
|**Wartość**|Wyświetla wartość liczbową symbolu.<br/><br/>Aby uzyskać więcej informacji, zobacz [ograniczenia wartości symboli](./changing-a-symbol-or-symbol-name-id.md).|
|**W użyciu**|Po wybraniu określa, że symbol jest używany przez co najmniej jeden zasób.<br/><br/>Zasób lub zasoby są wymienione w polu **używane przez** .|
|**Pokaż symbole tylko do odczytu**|Po wybraniu wyświetla zasoby tylko do odczytu.<br/><br/>Domyślnie w oknie dialogowym **symbol zasobu** są wyświetlane tylko zasoby, które można modyfikować w pliku skryptu zasobu, ale w przypadku wybrania tej opcji zasoby, które można modyfikować, są wyświetlane w postaci pogrubionego tekstu, a zasoby tylko do odczytu są wyświetlane w postaci zwykłego tekstu.|
|**Używane przez**|Wyświetla zasób lub zasoby przy użyciu symbolu wybranego na liście symbole.<br/><br/>Aby przejść do edytora dla danego zasobu, wybierz zasób w polu **używane przez** , a następnie wybierz pozycję **Wyświetl Użyj**.|
|**Nowe**|Otwiera okno dialogowe **Nowy symbol** , które pozwala zdefiniować nazwę i, w razie potrzeby, wartość nowego symbolicznego identyfikatora zasobu.|
|**Zmień**|Otwiera okno dialogowe **Zmień symbol** , które pozwala zmienić nazwę lub wartość symbolu.<br/><br/>Jeśli symbol dotyczy kontrolki lub zasobu w użyciu, symbol można zmienić tylko z odpowiedniego edytora zasobów. Aby uzyskać więcej informacji, zobacz [Zarządzanie symbolami](./changing-a-symbol-or-symbol-name-id.md).|
|**Wyświetl użycie**|Otwiera zasób zawierający symbol w odpowiednim edytorze zasobów.|

## <a name="create-symbols"></a>Tworzenie symboli

### <a name="to-create-a-new-symbol"></a>Aby utworzyć nowy symbol

1. W oknie dialogowym **symbole zasobów** wybierz pozycję **Nowy**.

1. W polu **Nazwa** wpisz nazwę symbolu.

1. Zaakceptuj przypisaną wartość symbolu lub wpisz nową wartość w polu **wartość** .

1. Wybierz **przycisk OK** , aby dodać nowy symbol do listy symboli.

> [!NOTE]
> Jeśli wpiszesz nazwę symbolu, który już istnieje, pojawi się okno komunikatu z informacją o tym, że symbol o tej nazwie jest już zdefiniowany. Nie można zdefiniować co najmniej dwóch symboli o tej samej nazwie, ale można zdefiniować różne symbole o tej samej wartości liczbowej.

## <a name="to-view-resource-symbols"></a>Aby wyświetlić symbole zasobów

W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)kliknij prawym przyciskiem myszy plik *. RC* , a następnie wybierz pozycję **symbole zasobów** , aby wyświetlić tabelę symboli zasobów w oknie dialogowym **symbole zasobów** .

> [!NOTE]
> Aby wyświetlić wstępnie zdefiniowane symbole, zaznacz pole wyboru **Pokaż symbole tylko do odczytu** .

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>Aby otworzyć Edytor zasobów dla danego symbolu

Podczas przeglądania symboli w **symbolach zasobów**warto uzyskać więcej informacji na temat sposobu użycia określonego symbolu. Przycisk **Wyświetl użycie** umożliwia szybkie uzyskanie tych informacji.

1. W oknie dialogowym **symbole zasobów** w polu **Nazwa** wybierz symbol.

1. W polu **używane przez** wybierz typ zasobu, który Cię interesuje.

1. Wybierz przycisk **Wyświetl Użyj** .

   Zasób pojawi się w odpowiednim oknie edytora.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Identyfikatory zasobów (symbole)](../windows/symbols-resource-identifiers.md)<br/>
[Instrukcje: Zarządzanie symbolami](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)<br/>
