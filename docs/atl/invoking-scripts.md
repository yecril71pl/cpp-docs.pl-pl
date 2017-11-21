---
title: "Wywoływanie skryptów (ATL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: StringRegister
dev_langs: C++
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c1fc6893b02dccff6bb30d7a20d1a2c1dce9fbb1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="invoking-scripts"></a>Skrypty wywołania
[Przy użyciu parametry wymienne (Rejestrator preprocesora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) omówiono mapy zastąpienia i uwagi metody rejestratora **AddReplacement**. Rejestrator ma osiem innych metod specyficzne dla skryptów, a wszystkie są opisane w poniższej tabeli.  
  
|Metoda|Składnia/opis|  
|------------|-------------------------|  
|**ResourceRegister**|**HRESULT ResourceRegister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);** <br /><br /> Rejestruje zawarte w module zasobu skryptu. *resFileName* wskazuje ścieżkę UNC do modułu, do samej siebie. `nID`i `szType` odpowiednio zawierają identyfikator i typu zasobu.|  
|**ResourceUnregister**|**HRESULT ResourceUnregister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);** <br /><br /> Wyrejestrowuje zawarte w module zasobu skryptu. *resFileName* wskazuje ścieżkę UNC do modułu, do samej siebie. `nID`i `szType` odpowiednio zawierają identyfikator i typu zasobu.|  
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***szID* **, LPCOLESTR** `szType` **);** <br /><br /> Rejestruje zawarte w module zasobu skryptu. *resFileName* wskazuje ścieżkę UNC do modułu, do samej siebie. *szID* i `szType` zawierają odpowiednio identyfikator ciągu i typu zasobu.|  
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***szID* **, LPCOLESTR** `szType` **);** <br /><br /> Wyrejestrowuje zawarte w module zasobu skryptu. *resFileName* wskazuje ścieżkę UNC do modułu, do samej siebie. *szID* i `szType` zawierają odpowiednio identyfikator ciągu i typu zasobu.|  
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR***fileName***);** <br /><br /> Rejestruje skryptu w pliku. *Nazwa pliku* jest ścieżką UNC do pliku, który zawiera (lub jej) skryptu zasobu.|  
|**FileUnregister**|**HRESULT FileUnregister (LPCOLESTR***fileName***);** <br /><br /> Wyrejestrowuje skryptu w pliku. *Nazwa pliku* jest ścieżką UNC do pliku, który zawiera (lub jej) skryptu zasobu.|  
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***danych***);** <br /><br /> Rejestruje skrypt w ciągu. *dane* zawiera sam skrypt.|  
|**StringUnregister**|**HRESULT StringUnregister (LPCOLESTR***danych***);** <br /><br /> Wyrejestrowuje skryptu w ciągu. *dane* zawiera sam skrypt.|  
  
 **ResourceRegisterSz** i **ResourceUnregisterSz**, są podobne do **ResourceRegister** i **ResourceUnregister**, ale zezwala na określanie Identyfikator ciągu.  
  
 Metody **FileRegister** i **FileUnregister** są przydatne, jeśli nie chcesz, aby skrypt w zasobie lub jeśli użytkownik chce skryptu w pliku. Metody **StringRegister** i **StringUnregister** pliku .rgs mają być przechowywane w ciągu dynamicznie przydzielonego dozwolonych.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)

