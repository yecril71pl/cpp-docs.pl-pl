---
title: Zalecenia dotyczące wybierania między ATL i MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
ms.openlocfilehash: e4e51f81bbdc54ff09980acfba22037df77abac9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259779"
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Zalecenia dotyczące wybierania między ATL i MFC

Podczas tworzenia składników i aplikacji, możesz wybrać dwóch metod — ATL i MFC (biblioteki klas Microsoft Foundation).

## <a name="using-atl"></a>Przy użyciu biblioteki ATL

ATL jest szybki i prosty sposób utworzyć składnik COM w języku C++ i obsługa o niewielkich rozmiarach. Użyj ATL, aby utworzyć formant, jeśli nie potrzebujesz wszystkich funkcji wbudowanych, który automatycznie zapewnia MFC.

## <a name="using-mfc"></a>Za pomocą MFC

MFC umożliwia tworzenie pełnych aplikacji, formanty ActiveX i dokumenty aktywne. Jeśli już utworzono kontrolkę z MFC, możesz kontynuować tworzenie w MFC. Podczas tworzenia nowej kontrolki, należy wziąć pod uwagę przy użyciu biblioteki ATL, jeśli nie potrzebujesz wszystkich funkcji wbudowanych w MFC.

## <a name="using-atl-in-an-mfc-project"></a>Przy użyciu biblioteki ATL w projekcie MFC

Możesz dodać obsługę przy użyciu biblioteki ATL w istniejącym projekcie MFC za pomocą kreatora. Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do ATL](../atl/introduction-to-atl.md)
