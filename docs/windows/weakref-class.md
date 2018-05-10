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
ms.openlocfilehash: ba7efc595be55b807cd3f044269db0debcb72407
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="weakref-class"></a>WeakRef — Klasa
Reprezentuje *słabe odwołanie* które mogą być używane przez tylko środowiska uruchomieniowego systemu Windows, nie klasycznego modelu COM. Słabe odwołanie reprezentuje obiekt, który może lub nie mogą być niedostępne.  
  
## <a name="syntax"></a>Składnia  
  
```  
class WeakRef : public ComPtr<IWeakReference>  
```  
  
## <a name="remarks"></a>Uwagi  
 Obiekt weakref — utrzymuje *silne odwołanie*, który jest skojarzony z obiektem i może być nieprawidłowa lub nieprawidłowy. Wywołaj metodę As() lub AsIID() uzyskanie silne odwołanie. Jeśli silne odwołanie jest prawidłowe, można uzyskać dostęp skojarzonego obiektu. Jeśli silne odwołanie jest nieprawidłowe (`nullptr`), skojarzonego obiektu jest niedostępny.  
  
 Obiekt weakref — zazwyczaj jest używana do reprezentowania obiekt, którego istnienie jest kontrolowany przez wątek zewnętrznych lub aplikacji. Na przykład utworzyć obiekt weakref — z odwołaniem do obiektu pliku. Gdy plik jest otwarty, silne odwołanie jest prawidłowe. Jednak jeśli plik zostanie zamknięty, silne odwołanie staje się nieprawidłowy.  
  
 Należy pamiętać, że zmiana zachowania [jako](../windows/weakref-as-method.md), [AsIID](../windows/weakref-asiid-method.md) i [CopyTo](../windows/weakref-copyto-method.md) metody w zestawie SDK systemu Windows 10. Wcześniej, po wywołaniu dowolnej z tych metod, można sprawdzić weakref — dla `nullptr` ustalenie, jeśli silne odwołanie pomyślnie uzyskano, zgodnie z poniższym kodem:  
  
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
  
 Powyższy kod nie działa, gdy za pomocą zestawu Windows 10 SDK (lub nowsza). Zamiast tego należy sprawdzić wskaźnika, która została przekazana dla `nullptr`.  
  
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
|[WeakRef::WeakRef, konstruktor](../windows/weakref-weakref-constructor.md)|Inicjuje nowe wystąpienie klasy weakref —.|  
|[WeakRef::~WeakRef, destruktor](../windows/weakref-tilde-weakref-destructor.md)|Deinitializes bieżące wystąpienie klasy weakref — klasa.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[WeakRef::As, metoda](../windows/weakref-as-method.md)|Ustawia określony parametr wskaźnika comptr — do reprezentowania określonego interfejsu.|  
|[WeakRef::AsIID, metoda](../windows/weakref-asiid-method.md)|Ustawia określony parametr wskaźnika comptr — do reprezentowania identyfikator określonego interfejsu.|  
|[WeakRef::CopyTo, metoda](../windows/weakref-copyto-method.md)|Przypisuje wskaźnik interfejsu, jeśli jest dostępny do zmiennej wskaźnikowej określony.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator WeakRef::operator&](../windows/weakref-operator-ampersand-operator.md)|Zwraca obiekt comptrref — reprezentujący bieżący obiekt weakref —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ComPtr`  
  
 `WeakRef`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)