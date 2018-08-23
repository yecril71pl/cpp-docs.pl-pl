---
title: Wstępnie zdefiniowane symbole Win32 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols, Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8578692701d6f9037ed40ed9ece34c79ca7f2275
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592791"
---
# <a name="win32-predefined-symbols"></a>Wstępnie zdefiniowane symbole Win32

Te symbole są zdefiniowane w plikach nagłówkowych Win32 i obsługują standardowe funkcje aplikacji Windows i akcje. Te symbole są głównie używane wspólnych elementów interfejsu użytkownika. Podczas pracy z kontrolkami w edytorach zasobów te symbole pojawią się w [okno właściwości](/visualstudio/ide/reference/properties-window) skojarzone z wspólnych formantów. Na przykład jeśli ikony aplikacji powinien być wyświetlany pasek narzędzi, ikona będzie skojarzona z symbolem IDI_SMALL w **okno właściwości**.

|||
|-|-|
|IDABORT|Sterowania: Przycisk Przerwij pola okna dialogowego|
|IDC_STATIC|Kontrola: Tekst statyczny w oknie dialogowym|
|IDCANCEL|Sterowania: Przycisk Anuluj okno dialogowe|
|IDD_ABOUTBOX|Okno dialogowe: Produkt, okno dialogowe|
|IDI_PROJECTNAME|Ikona: Bieżąca ikona projektu|
|IDI_SMALL|Ikona: Bieżący projekt małe ikony|
|IDIGNORE|Kontrola: Używany przycisk Ignoruj w oknach dialogowych|
|IDM_ABOUT|Element menu: Używany z Pomoc... Temat...|
|IDM_EXIT|Element menu: Używany z pliku... Zakończ...|
|IDNO|Sterowania: Okno dialogowe ma przycisku|
|IDOK|Sterowania: Przycisk pola OK okno dialogowe|
|IDRETRY|Sterowania: Przycisk Ponów okno dialogowe|
|IDS_APP_TITLE|Ciąg: Bieżąca nazwa aplikacji|
|IDYES|Kontrola: Okno dialogowe tak przycisku.|

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)  
[Symbole: identyfikatory zasobów](../windows/symbols-resource-identifiers.md)