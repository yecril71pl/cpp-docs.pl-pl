---
title: Korzystanie z biblioteki szablonów (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- template libraries
ms.assetid: 5e80ec6e-a61c-41ce-b34b-9a6252c46265
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91a9c10bef285780ded145e33800ebd3db198827
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754800"
---
# <a name="using-a-template-library"></a>Korzystanie z biblioteki szablonów

Szablon jest nieco takich jak makra. Podobnie jak w przypadku makra, wywoływania szablonu powoduje, że rozwinąć (za pomocą odpowiednich parametrów podstawiania) do kodu, które zostały napisane. Jednak szablonu jest przesyłany dalej niż ten element, aby umożliwić tworzenie nowych klas na podstawie typów, które są przekazywane jako parametry. Te nowe klasy implementuje bezpieczne sposoby wykonywania operacji wyrażoną w kodzie szablonu.

Szablon biblioteki, takie jak biblioteki ATL różnią się od tradycyjnych bibliotek klas języka C++, w tym, że są zazwyczaj dostarczane tylko jako kod źródłowy (lub jako kod źródłowy z małym, obsługa w czasie wykonywania) i nie są założenia lub niekoniecznie hierarchiczne. Zamiast pochodząca od klasy funkcje, które chcesz pobrać, Utwórz wystąpienie klasy z szablonu.

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do ATL](../atl/introduction-to-atl.md)

