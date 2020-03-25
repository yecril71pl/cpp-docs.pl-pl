---
title: Ostrzeżenie RW4004 kompilatora zasobów
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: ca0fb271a5ab43994ec37cc8d59c33877903f6e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182347"
---
# <a name="resource-compiler-warning-rw4004"></a>Ostrzeżenie RW4004 kompilatora zasobów

Znak ASCII nie jest odpowiednikiem kodu klucza wirtualnego

Literał ciągu został użyty dla kodu klucza wirtualnego w akceleratorze typu standardowym VIRTKEY.

To ostrzeżenie pozwala kontynuować, ale należy pamiętać, że wygenerowane klucze akceleratora mogą być niezgodne z podanym ciągiem. (VIRTKEYs używają innych kodów kluczy niż akceleratory ASCII).

Gdy literały ciągu są syntaktycznie prawidłowe, można upewnić się, że odpowiedni akcelerator jest uzyskiwany przy użyciu **VK_\* #define** wartości w systemie Windows. h.
