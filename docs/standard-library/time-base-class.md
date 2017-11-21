---
title: "time_base — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: locale/std::time_base
dev_langs: C++
helpviewer_keywords: time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a1e7fca06a16cf879ab46a132a6f35b79532cc6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="timebase-class"></a>time_base — Klasa
Klasa służy jako klasę podstawową dla aspekty time_get — klasa szablonu, definiowanie tylko typ wyliczeniowy **dateorder** i kilka stałych tego typu.  
  
## <a name="syntax"></a>Składnia  
  
```
class time_base : public locale::facet {
public:
    enum dateorder {no_order,
    dmy,
 mdy,
    ymd,
 ydm};
    time_base(
 size_t _Refs = 0)
 ~time_base();

};
```  
  
## <a name="remarks"></a>Uwagi  
 Każdy stała charakteryzuje inny sposób, aby uporządkować składniki daty. Stałe są:  
  
- **no_order** określa nie określonej kolejności.  
  
- **dmy** określa kolejność dzień, miesiąc, a następnie roku, tak jak 2 grudnia 1979.  
  
- **MDY** określa kolejność miesiąc, dzień, a następnie roku, tak jak 2 grudnia 1979.  
  
- **YMD** określa kolejność rok, miesiąc, a następnie dziennie, tak jak 1979/12/2.  
  
- **ydm** określa kolejności roku, dzień, miesiąc, tak jak gru 1979:2.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



