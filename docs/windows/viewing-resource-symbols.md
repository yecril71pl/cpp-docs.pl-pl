---
title: Wyświetlanie symboli zasobów (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
helpviewer_keywords:
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 4bcc06d9-7d36-486a-8a37-71da0541643c
ms.openlocfilehash: e61269261fc9172288f1edf58419009178c755d9
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763976"
---
# <a name="viewing-resource-symbols"></a>Wyświetlanie symboli zasobów

**Symboli zasobów** C++, okno dialogowe umożliwia dodawanie nowych symboli zasobów, zmienianie symboli, które są wyświetlane, lub przejdź do lokalizacji w kodzie źródłowym, w której symbol jest używany.

Okno dialogowe zawiera następujące właściwości:

|Właściwość|Opis|
|---|---|
|**Nazwa**|Wyświetla nazwę symbolu. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md).|
|**Wartość**|Wyświetlana jest wartość liczbowa symbolu. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md).|
|**W użyciu**|Po wybraniu Określa, czy symbol jest używany przez co najmniej jednego zasobu. Zasób lub zasoby są wymienione w używana przez pole.|
|**Pokaż symbole tylko do odczytu**|Po wybraniu Wyświetla zasoby tylko do odczytu. Domyślnie **Symbol zasobu** okno dialogowe wyświetla tylko zasoby można modyfikować w pliku skryptu zasobu, ale z wybraniu tej opcji można modyfikować zasoby są wyświetlane pogrubioną czcionką i zasoby tylko do odczytu są wyświetlane w postaci zwykłego tekstu.|
|**Używane przez**|Wyświetla zasobami przy użyciu symbolu zaznaczony na liście symboli. Aby przejść do edytora dla danego zasobu, wybierz zasób w **używane przez** pole, a następnie kliknij przycisk **Wyświetl użycie**. Aby uzyskać więcej informacji, zobacz [Otwieranie Edytora zasobów dla danego symbolu](../windows/opening-the-resource-editor-for-a-given-symbol.md).|
|**Nowy**|Otwiera **nowy Symbol** okno dialogowe, w którym można zdefiniować nazwę i, jeśli to konieczne, wartość dla nowego identyfikatora zasobu symboliczne. Aby uzyskać więcej informacji, zobacz [tworzenie nowych symboli](../windows/creating-new-symbols.md).|
|**Change**|Otwiera **Zmień Symbol** okno dialogowe, które umożliwia zmianę nazwy lub wartości symbolu. Jeśli symbol jest dla formantu lub zasobów w użyciu, symbolu można zmienić tylko za pomocą odpowiedniego edytora zasobów. Aby uzyskać więcej informacji, zobacz [zmiana nieprzypisanych symboli](../windows/changing-unassigned-symbols.md).|
|**Wyświetl użycie**|Zostanie otwarty zasób, który zawiera symbol w edytorze odpowiednich zasobów. Aby uzyskać więcej informacji, zobacz [Otwieranie Edytora zasobów dla danego symbolu](../windows/opening-the-resource-editor-for-a-given-symbol.md).|

## <a name="to-view-resource-symbols"></a>Aby wyświetlić symboli zasobów

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Wybierz **symboli zasobów** z menu skrótów, aby wyświetlić tabelę symboli zasobów w **symboli zasobów** okno dialogowe.

   > [!NOTE]
   > Aby wyświetlić wstępnie zdefiniowane symbole, zapoznaj się z **Pokaż symbole tylko do odczytu** pole wyboru.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Symbole: identyfikatory zasobów](../windows/symbols-resource-identifiers.md)