---
title: para (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::pair
dev_langs:
- C++
helpviewer_keywords:
- pair class [STL/CLR]
ms.assetid: 3326b4d9-a52a-49e5-8103-9aa5e8b352de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a8c4ae8ee9fbcfddd6009d4e91134d59a9a02cc9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="pair-stlclr"></a>pair (STL/CLR)
Klasa szablonu opisuje obiekt, który opakowuje pary wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### <a name="parameters"></a>Parametry  
 Wartość1  
 Typ pierwszego zakodowana wartość.  
  
 Wartość2  
 Typ drugiego zakodowana wartość.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[pair::first_type (STL/CLR)](../dotnet/pair-first-type-stl-clr.md)|Typ pierwszego zakodowana wartość.|  
|[pair::second_type (STL/CLR)](../dotnet/pair-second-type-stl-clr.md)|Typ drugiego zakodowana wartość.|  
  
|Element członkowski obiektu|Opis|  
|-------------------|-----------------|  
|[pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)|Pierwszy przechowywana wartość.|  
|[pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)|Druga wartość przechowywane.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[pair::pair (STL/CLR)](../dotnet/pair-pair-stl-clr.md)|Tworzy obiekt pary.|  
|[pair::swap (STL/CLR)](../dotnet/pair-swap-stl-clr.md)|Zamienia zawartość dwie pary.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[pair::operator= (STL/CLR)](../dotnet/pair-operator-assign-stl-clr.md)|Zastępuje para przechowywanej wartości.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przechowuje pary wartości. Klasa szablonu jest używana do łączenia dwóch wartości w jeden obiekt. Należy pamiętać, że `cliext::pair` (opisanych poniżej) magazynów tylko typy zarządzane, aby przechowywać pary niezarządzane przy użyciu typów `std::pair`, zadeklarowanych w `<utility>`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/Narzędzia >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [make_pair (STL/CLR)](../dotnet/make-pair-stl-clr.md)