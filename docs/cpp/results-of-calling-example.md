---
title: Wyniki przykładu wywołania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cc5d5f96b5ffabd5397f26b6ff1372232fe0cd6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421422"
---
# <a name="results-of-calling-example"></a>Wyniki przykładu wywołania
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
  
## <a name="cdecl"></a>__cdecl  
 Nazwy ozdobione funkcji C jest "_MyFunc."  
  
 ![Używana konwencja wywołania CDECL](../cpp/media/vc37i01.gif "vc37I01")  
Konwencja wywoływania __cdecl  
  
## <a name="stdcall-and-thiscall"></a>__stdcall i thiscall  
 Nazwy ozdobione C (`__stdcall`) jest "_MyFunc@20." Nazwy ozdobione C++ jest zastrzeżone.  
  
 ![&#95;&#95;STDCALL i Konwencje wywoływania thiscall](../cpp/media/vc37i02.gif "vc37I02")  
__Stdcall i thiscall Konwencje wywoływania  
  
## <a name="fastcall"></a>__fastcall  
 Nazwy ozdobione C (`__fastcall`) jest "@MyFunc@20." Nazwy ozdobione C++ jest zastrzeżone.  
  
 ![Konwencja wywoływania &#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03")  
Konwencja wywoływania __fastcall  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Przykład wywołania: prototyp funkcji i wywołanie](../cpp/calling-example-function-prototype-and-call.md)