---
title: Ostrzeżenie kompilatora (poziom 3) C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 38b346e0a90729bda431b9cb578a03806be1ea4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198981"
---
# <a name="compiler-warning-level-3-c4192"></a>Ostrzeżenie kompilatora (poziom 3) C4192

automatyczne wykluczanie "name" podczas importowania biblioteki typów "Library"

Biblioteka `#import` zawiera element, *nazwę*, który jest również zdefiniowany w nagłówkach systemu Win32. Ze względu na ograniczenia bibliotek typów, nazwy takie jak **IUnknown** lub GUID są często definiowane w bibliotece typów, duplikując definicję z nagłówków systemowych. `#import` wykryje te elementy i odmówi, że zostaną one dołączone do plików nagłówkowych. tlh i. tli.

Aby zastąpić to zachowanie, użyj atrybutów `#import` [no_auto_exclude](../../preprocessor/no-auto-exclude.md) i [include ()](../../preprocessor/include-parens.md).
