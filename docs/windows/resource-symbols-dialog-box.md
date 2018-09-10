---
title: Symbole zasobu, okno dialogowe (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resourcesymbols
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 064fb9adce8b41c13709819f7ce0b7c515fea12a
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313172"
---
# <a name="resource-symbols-dialog-box-c"></a>Okno dialogowe symboli zasobów (C++)

**Symboli zasobów** C++, okno dialogowe umożliwia dodawanie nowych symboli zasobów, zmienianie symboli, które są wyświetlane, lub przejdź do lokalizacji w kodzie źródłowym, w której symbol jest używany.

**Nazwa**  
Wyświetla nazwę symbolu. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md).

**Wartość**  
Wyświetlana jest wartość liczbowa symbolu. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md).

**W użyciu**  
Po wybraniu Określa, czy symbol jest używany przez co najmniej jednego zasobu. Zasób lub zasoby są wymienione w używana przez pole.

**Pokaż symbole tylko do odczytu**  
Po wybraniu Wyświetla zasoby tylko do odczytu. Domyślnie **Symbol zasobu** okno dialogowe wyświetla tylko zasoby można modyfikować w pliku skryptu zasobu, ale z wybraniu tej opcji można modyfikować zasoby są wyświetlane pogrubioną czcionką i zasoby tylko do odczytu są wyświetlane w postaci zwykłego tekstu.

**Używane przez**  
Wyświetla zasobami przy użyciu symbolu zaznaczony na liście symboli. Aby przejść do edytora dla danego zasobu, wybierz zasób w **używane przez** pole, a następnie kliknij przycisk **Wyświetl użycie**. Aby uzyskać więcej informacji, zobacz [Otwieranie Edytora zasobów dla danego symbolu](../windows/opening-the-resource-editor-for-a-given-symbol.md).

**Nowy**  
Otwiera **nowy Symbol** okno dialogowe, w którym można zdefiniować nazwę i, jeśli to konieczne, wartość dla nowego identyfikatora zasobu symboliczne. Aby uzyskać więcej informacji, zobacz [tworzenie nowych symboli](../windows/creating-new-symbols.md).

**Zmiany**  
Otwiera **Zmień Symbol** okno dialogowe, które umożliwia zmianę nazwy lub wartości symbolu. Jeśli symbol jest dla formantu lub zasobów w użyciu, symbolu można zmienić tylko za pomocą odpowiedniego edytora zasobów. Aby uzyskać więcej informacji, zobacz [zmiana nieprzypisanych symboli](../windows/changing-unassigned-symbols.md).

**Wyświetl użycie**  
Zostanie otwarty zasób, który zawiera symbol w edytorze odpowiednich zasobów. Aby uzyskać więcej informacji, zobacz [Otwieranie Edytora zasobów dla danego symbolu](../windows/opening-the-resource-editor-for-a-given-symbol.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Wyświetlanie symboli zasobów](../windows/viewing-resource-symbols.md)