---
title: Relacja z interfejsem API języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 027a14213f173bdc6be5fc34e9fd4faf0eba8023
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415157"
---
# <a name="relationship-to-the-c-language-api"></a>Relacja z interfejsem API języka C

Jedna właściwość, która ustawia biblioteki Microsoft Foundation Class (MFC) niezależnie od innych bibliotek klas dla Windows jest bardzo ścisłej mapowania interfejsu API Windows napisanych w języku C. Dodatkowo można zazwyczaj łączyć wywołania do biblioteki klas za darmo z bezpośrednim wywołaniem do interfejsu API Windows. Dostęp bezpośredni, jednak oznacza, że klasy są całkowitego zastąpienia dla tego interfejsu API. Deweloperzy nadal od czasu do czasu należy wykonywać bezpośrednich wywołań do niektórych funkcji Windows takich jak [SetCursor](/windows/desktop/api/winuser/nf-winuser-setcursor) i [GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics), na przykład. Funkcja Windows jest otoczony przez funkcji składowej klasy, tylko wtedy, gdy z zalet jasny sposób.

Ponieważ czasami trzeba wykonać natywnych wywołania funkcji Windows powinna mieć dostęp do dokumentacji interfejsu API Windows języka C. Ta dokumentacja jest dołączony do programu Microsoft Visual C++.

> [!NOTE]
>  Aby zapoznać się z omówieniem sposób działania w ramach biblioteki MFC, zobacz [używanie klas do pisania aplikacji dla Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Zobacz też

[Ogólne zasady projektowania klas](../mfc/general-class-design-philosophy.md)
