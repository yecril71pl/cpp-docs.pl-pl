---
title: Wątkowość modeli i klasy sekcje krytyczne (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- vc.atl.threads.models
dev_langs:
- C++
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37172c0080664f496bdf5d5c7c0ebecbd8f77898
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="threading-models-and-critical-sections-classes"></a>Wątkowość modeli i klasy sekcje krytyczne
Poniższe klasy definiują wątkowość modelu i sekcja krytyczna:  
  
-   [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) implementuje wątków w puli, modelu typu apartment serwer COM.  
  
-   [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) udostępnia metody wykonywania wątków w puli, modelu typu apartment serwer COM.  
  
-   [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) udostępnia bezpieczne wątkowo metody zwiększanie oraz zmniejszanie zmiennej. Zawiera sekcja krytyczna.  
  
-   [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) udostępnia bezpieczne wątkowo metody zwiększanie oraz zmniejszanie zmiennej. Nie zawiera sekcja krytyczna.  
  
-   [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) udostępnia metody zwiększanie oraz zmniejszanie zmiennej. Nie zawiera sekcja krytyczna.  
  
-   [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) określa odpowiedniej klasy model wątkowy dla klasy pojedynczego obiektu.  
  
-   [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel) określa odpowiedniej klasy model wątkowy dla obiekt, który jest ogólnie dostępna.  
  
-   [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) zawiera metody uzyskiwania i zwalniania sekcja krytyczna. Sekcja krytyczna automatycznie został zainicjowany.  
  
-   [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) zawiera metody uzyskiwania i zwalniania sekcja krytyczna. Sekcja krytyczna musi być jawnie zainicjowany.  
  
-   [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) odzwierciedla metod w `CComCriticalSection` bez podawania sekcja krytyczna. Metody w `CComFakeCriticalSection` nic nie rób.  
  
-   [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) udostępnia funkcję tworzenia dla wątku CRT. Użyj tej klasy, jeśli wątek użyje funkcji CRT.  
  
-   [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) udostępnia funkcję tworzenia dla wątku systemu Windows. Użyj tej klasy, jeśli wątek nie będzie używać funkcji CRT.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../atl/atl-class-overview.md)

