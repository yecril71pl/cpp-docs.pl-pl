---
title: 'Zarządzanie pamięcią: alokacja stosu'
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC], detecting leaks
- delete operator [MFC], using with debug MFC
- heap allocation [MFC], described
- memory allocation [MFC], heap memory
- memory leaks [MFC], detecting
- new operator [MFC], using with debug MFC
- heap allocation [MFC]
- detecting memory leaks [MFC]
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
ms.openlocfilehash: 1f0b07a0a3439faba71078af1e2d7d1559a42b41
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626284"
---
# <a name="memory-management-heap-allocation"></a>Zarządzanie pamięcią: alokacja stosu

Stos jest zarezerwowany dla potrzeb alokacji pamięci programu. Jest to obszar poza kodem programu i stosem. W przypadku typowych programów C użycie funkcji **malloc** i **Free** umożliwia przydzielanie i cofanie alokacji pamięci sterty. Wersja debugowania MFC zawiera zmodyfikowane wersje wbudowanych operatorów języka C++ **New** i **delete** w celu przydzielania i dealokacji obiektów w pamięci sterty.

W przypadku korzystania z funkcji **New** i **delete** zamiast opcji **malloc** i **Free**można korzystać z ulepszeń debugowania zarządzania pamięcią w bibliotece klas, co może być przydatne w przypadku wykrywania przecieków pamięci. Podczas kompilowania programu przy użyciu wersji MFC, standardowe wersje operatorów **New** i **delete** zapewniają efektywny sposób przydzielenia i cofnięcia przydziału pamięci (wersja wersji MFC nie udostępnia zmodyfikowanych wersji tych operatorów).

Należy zauważyć, że łączny rozmiar obiektów przydzielonych na stercie jest ograniczony tylko przez dostępną pamięć wirtualną systemu.

## <a name="see-also"></a>Zobacz też

[Zarządzanie pamięcią](memory-management.md)
