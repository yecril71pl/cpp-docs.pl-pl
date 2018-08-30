---
title: Tworzenie nowych symboli | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.creating
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box
- symbols, creating
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d84eef4c91442eedc830fdee836dc5d950b5eae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209593"
---
# <a name="creating-new-symbols"></a>Tworzenie nowych symboli

Gdy rozpoczynamy od nowego projektu, może okazać się wygodne do mapowania nazwy symboli, które należy spełnić przed tworzenia zasobów, do których zostanie przypisany.

### <a name="to-create-a-new-symbol-using-the-resource-symbols-dialog-box"></a>Aby utworzyć nowy symbol za pomocą okno dialogowe symboli zasobów

1. W [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md), wybierz **New**.

2. W **nazwa** wpisz nazwę symbolu.

3. Zaakceptuj wartość przypisanej symboli.

   —lub—

   W **wartość** wpisz nową wartość.

4. Kliknij przycisk **OK** Aby dodać nowy symbol do lista symboli.

Jeśli wpiszesz nazwę symbolu, który już istnieje, pojawia się komunikat z informacją, że symbol o tej nazwie jest już zdefiniowany. Nie można zdefiniować co najmniej dwóch symbole o takiej samej nazwie, ale można zdefiniować różne symboli z taką samą wartość liczbową. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md) i [ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Instrukcje dotyczące ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów wyświetlania statycznych zasobów i przydzielanie zasobów ciągów do właściwości.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Wyświetlanie symboli zasobów](../windows/viewing-resource-symbols.md)  
[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)