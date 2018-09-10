---
title: Właściwość modyfikatora akceleratora (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 793e02b4ac083d6fe84ba2cc76ee340bcf2484e9
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316058"
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

[Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)  
[Edytor klawiszy skrótów](../windows/accelerator-editor.md)