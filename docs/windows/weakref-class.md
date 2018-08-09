---
title: Weakref — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef class
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f56b35ffb53da8947982359174784a0dbb3cef85
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012589"
---
# <a name="weakref-class"></a>WeakRef — Klasa
Reprezentuje *słabe odwołanie* mogą służyć tylko Windows środowisko wykonawcze, nie Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class WeakRef : public ComPtr<IWeakReference>  
```  
  
## <a name="remarks"></a>Uwagi  
 A **WeakRef** obiekt zachowuje *silne odwołanie*, który jest skojarzony z obiektem i może być prawidłowy lub nieprawidłowy. Wywołaj `As()` lub `AsIID()` metodę, aby uzyskać silne odwołanie. Gdy silne odwołanie są poprawne, dostęp skojarzonego obiektu. Jeśli silne odwołanie jest nieprawidłowe (**nullptr**), skojarzonego obiektu jest niedostępny.  
  
 A **WeakRef** obiekt jest zwykle używana do reprezentowania obiekt, którego istnienie jest kontrolowane przez zewnętrzny wątek lub aplikację. Na przykład, utworzyć **WeakRef** obiektu z odwołaniem do obiektu pliku. Gdy plik jest otwarty, silne odwołanie jest prawidłowy. Ale jeśli ten plik będzie zamknięty, silne odwołanie staje się nieprawidłowy.  
  
 Należy pamiętać, że zmiana zachowania [jako](../windows/weakref-as-method.md), [asiid —](../windows/weakref-asiid-method.md) i [CopyTo](../windows/weakref-copyto-method.md) metody w zestawie SDK systemu Windows 10. Wcześniej, po wywołaniu dowolnej z tych metod, możesz sprawdzić WeakRef dla **nullptr** ustalenie, jeśli silne odwołanie pomyślnie uzyskano, zgodnie z poniższym kodem:  
  
```cpp  
WeakRef wr;  
strongComptrRef.AsWeak(&wr);  
  
// Now suppose that the object strongComPtrRef points to no longer exists  
// and the following code tries to get a strong ref from the weak ref:  
ComPtr<ISomeInterface> strongRef;  
HRESULT hr = wr.As(&strongRef);  
  
// This check won't work with the Windows 10 SDK version of the library.  
// Check the input pointer instead.  
if(wr == nullptr)  
{  
    wprintf(L"Couldn’t get strong ref!");  
}  
```  
  
 Powyższy kod nie działa, korzystając z zestawu Windows 10 SDK (lub nowszego). Zamiast tego należy sprawdzić wskaźnika, która została przekazana dla **nullptr**.  
  
```cpp  
if (strongRef == nullptr)  
{  
    wprintf(L"Couldn't get strong ref!");  
}  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[WeakRef::WeakRef, konstruktor](../windows/weakref-weakref-constructor.md)|Inicjuje nowe wystąpienie klasy **WeakRef** klasy.|  
|[WeakRef::~WeakRef, destruktor](../windows/weakref-tilde-weakref-destructor.md)|Deinicjuje bieżące wystąpienie **WeakRef** klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[WeakRef::As, metoda](../windows/weakref-as-method.md)|Ustawia określony `ComPtr` parametru wskaźnika do reprezentowania określonego interfejsu.|  
|[WeakRef::AsIID, metoda](../windows/weakref-asiid-method.md)|Ustawia określony `ComPtr` parametru wskaźnika do reprezentowania identyfikatora określonego interfejsu.|  
|[WeakRef::CopyTo, metoda](../windows/weakref-copyto-method.md)|Przypisuje wskaźnik interfejsu, jeśli to możliwe, do zmiennej wskaźnika określonej.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator WeakRef::operator&](../windows/weakref-operator-ampersand-operator.md)|Zwraca `ComPtrRef` obiekt, który reprezentuje bieżący **WeakRef** obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ComPtr`  
  
 `WeakRef`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)