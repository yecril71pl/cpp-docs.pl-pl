---
title: 'Porady: wyszukiwanie symboli w zasobach (C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 51b2045a1605a37fa9c0d17fdc0c9456652345bd
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314199"
---
# <a name="how-to-search-for-symbols-in-resources-c"></a>Porady: wyszukiwanie symboli w zasobach (C++)

### <a name="to-find-symbols-in-resources"></a>Aby znaleźć symboli w zasobach

1. Z **Edytuj** menu, wybierz **Znajdź Symbol**.

2. W [Znajdź Symbol — okno dialogowe](/visualstudio/ide/go-to)w **Znajdź** Wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz klawisza skrótu do wyszukania (na przykład ID_ACCEL1).

   > [!TIP]
   > Aby użyć [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) wyszukiwania, należy użyć [Znajdź w plikach — polecenie](/visualstudio/ide/reference/find-command) z **Edytuj** menu zamiast **Znajdź Symbol**polecenia. Aby włączyć wyrażeń regularnych, konieczne jest posiadanie **użycia: wyrażeń regularnych** zaznaczone pole wyboru w [okno dialogowe Znajdź](/visualstudio/ide/finding-and-replacing-text). Następnie możesz kliknąć przycisk strzałki w dół po prawej stronie **Znajdź** pole, aby wyświetlić listę wyrażeń regularnych wyszukiwania. Po wybraniu wyrażenia z tej listy, zostanie zastąpiony jako wyszukiwany tekst w **Znajdź** pole.

3. Wybierz dowolny z **znaleźć** opcje.

4. Kliknij przycisk **Znajdź następny**.

   > [!NOTE]
   > Nie można wyszukiwać symbole w ciągu, akcelerator lub zasobów binarnych.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Instrukcje dotyczące ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów wyświetlania statycznych zasobów i przydzielanie zasobów ciągów do właściwości.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Symbole: identyfikatory zasobów](../windows/symbols-resource-identifiers.md)  
[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Edytory zasobów](../windows/resource-editors.md)