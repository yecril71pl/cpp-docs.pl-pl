---
title: Zalecenia dotyczące wybierania między ATL i MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a9bbf30c728b6562da0c56c25b177697f0882a5
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762128"
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Zalecenia dotyczące wybierania między ATL i MFC

Podczas tworzenia składników i aplikacji, możesz wybrać dwóch metod — ATL i MFC (biblioteki klas Microsoft Foundation).

## <a name="using-atl"></a>Przy użyciu biblioteki ATL

ATL jest szybki i prosty sposób utworzyć składnik COM w języku C++ i obsługa o niewielkich rozmiarach. Użyj ATL, aby utworzyć formant, jeśli nie potrzebujesz wszystkich funkcji wbudowanych, który automatycznie zapewnia MFC.

## <a name="using-mfc"></a>Za pomocą MFC

MFC umożliwia tworzenie pełnych aplikacji, formanty ActiveX i dokumenty aktywne. Jeśli już utworzono kontrolkę z MFC, możesz kontynuować tworzenie w MFC. Podczas tworzenia nowej kontrolki, należy wziąć pod uwagę przy użyciu biblioteki ATL, jeśli nie potrzebujesz wszystkich funkcji wbudowanych w MFC.

## <a name="using-atl-in-an-mfc-project"></a>Przy użyciu biblioteki ATL w projekcie MFC

Możesz dodać obsługę przy użyciu biblioteki ATL w istniejącym projekcie MFC za pomocą kreatora. Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do ATL](../atl/introduction-to-atl.md)

