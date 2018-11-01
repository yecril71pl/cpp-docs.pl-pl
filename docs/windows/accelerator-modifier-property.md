---
title: Właściwość modyfikatora akceleratora (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
ms.openlocfilehash: f9dfcbde68d2b3d1ebdd1b94aa40339bbc0ff4e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650706"
---
# <a name="accelerator-modifier-property-c"></a>Właściwość modyfikatora akceleratora (C++)

Dostępne są następujące wpisy prawne dla właściwości modyfikujące w tabeli akceleratora.

|Wartość|Opis|
|-----------|-----------------|
|**Brak**|Użytkownik naciśnie tylko **klucz** wartość. Najbardziej efektywne służy to przy użyciu wartości ASCII/ANSI 001 za pośrednictwem 026, który jest interpretowany jako ^ od A do ^ Z (CTRL-A za pomocą klawisze CTRL + Z).|
|**ALT**|Użytkownik musi nacisnąć klawisz **Alt** klucza przed **klucz** wartość.|
|**CTRL**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
|**SHIFT**|Użytkownik musi nacisnąć klawisz **Shift** klucza przed **klucz** wartość.|
|**Ctrl + Alt**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza i **Alt** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
|**Ctrl + Shift**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza i **Shift** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
|**Alt + Shift**|Użytkownik musi nacisnąć klawisz **Alt** klucza i **Shift** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
|**Ctrl + Alt + Shift**|Użytkownik musi nacisnąć klawisz **Ctrl**, **Alt**, i **Shift** przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)<br/>
[Edytor klawiszy skrótów](../windows/accelerator-editor.md)