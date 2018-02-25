---
title: "Schedulegroup — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
dev_langs:
- C++
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b2ba16ff0e17a0a6e8cc63cefaebe1e66a93af7c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="schedulegroup-class"></a>ScheduleGroup — Klasa
Reprezentuje abstrakcję do grupy harmonogramu. Grupy harmonogramu uporządkowania zbioru powiązanych pracy tego korzyści z planowany blisko siebie tymczasowo, wykonując inne zadanie w tej samej grupy przed przejściem do innej grupy lub od, wykonując wielu elementów w tej samej grupie na tym samym Lub gniazda fizycznego węzła NUMA.  
  
## <a name="syntax"></a>Składnia  
  
```
class ScheduleGroup;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[~ ScheduleGroup — destruktor](#dtor)||  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Id](#id)|Zwraca identyfikator grupy harmonogram, który jest unikatowy w ramach harmonogramu, do której należy grupa.|  
|[Dokumentacja](#reference)|Zwiększa liczbę harmonogram grupy odwołania.|  
|[Wersja](#release)|Zmniejsza liczba odwołanie do grupy harmonogramu.|  
|[ScheduleTask](#scheduletask)|Zaplanowane zadania lekki w obrębie grupy harmonogramu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ScheduleGroup`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="id"></a> Id 

 Zwraca identyfikator grupy harmonogram, który jest unikatowy w ramach harmonogramu, do której należy grupa.  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator grupy harmonogram, który jest unikatowy w ramach harmonogramu, do której należy grupa.  
  
##  <a name="operator_delete"></a> Usuwanie operatora 

 A `ScheduleGroup` obiekt zostanie zniszczony wewnętrznie przez środowisko uruchomieniowe po udostępnieniu wszystkie zewnętrzne odwołania do niego. Nie można być jawnie usunąć.  
  
```
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
 const char *,
    int);
```    
  
### <a name="parameters"></a>Parametry  
 `_PObject`  
 Wskaźnik do obiektu, który ma zostać usunięty.  
  
##  <a name="reference"></a> Odwołanie 

 Zwiększa liczbę harmonogram grupy odwołania.  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba odwołań nowo zwiększany.  
  
### <a name="remarks"></a>Uwagi  
 Służy to zwykle zarządzać okresem istnienia grupy harmonogramu dla kompozycji. Grupy harmonogramu liczebności referencyjnej grupy harmonogramu przypada na zero, są usuwane w czasie wykonywania. Grupy harmonogramu utworzone za pomocą [CurrentScheduler::CreateScheduleGroup](currentscheduler-class.md#createschedulegroup) metody, lub [Scheduler::CreateScheduleGroup](scheduler-class.md#createschedulegroup) metody rozpoczyna się od jednego licznika odwołań.  
  
##  <a name="release"></a> Zlecenia 

 Zmniejsza liczba odwołanie do grupy harmonogramu.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba odwołań nowo zmniejszany.  
  
### <a name="remarks"></a>Uwagi  
 Służy to zwykle zarządzać okresem istnienia grupy harmonogramu dla kompozycji. Grupy harmonogramu liczebności referencyjnej grupy harmonogramu przypada na zero, są usuwane w czasie wykonywania. Po wywołaniu `Release` metody określoną liczbę razy, aby usunąć Tworzenie odwołania liczbę i wszelkie dodatkowe informacje umieszczona przy użyciu `Reference` metody, nie może wykorzystywać grupę harmonogram dalej. W ten sposób spowoduje niezdefiniowane zachowanie.  
  
 Grupy harmonogramu jest skojarzony z wystąpieniem określonego harmonogramu. Należy się upewnić, że wszystkie odwołania do grupy harmonogramu są wydawane zanim wszystkie odwołania do harmonogramu są wydawane, ponieważ to drugie może skutkować harmonogramu niszczony. Wykonywanie w przeciwnym razie wynikiem niezdefiniowane zachowanie.  
  
##  <a name="dtor"></a> ~ScheduleGroup 

```
virtual ~ScheduleGroup();
```  
  
##  <a name="scheduletask"></a> ScheduleTask 

 Zaplanowane zadania lekki w obrębie grupy harmonogramu.  
  
```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Proc`  
 Wskaźnik do funkcji w celu wykonania do wykonywania zadań lekki treści.  
  
 `_Data`  
 Void wskaźnik do danych, który zostanie przekazany jako parametr do treści zadania.  
  
### <a name="remarks"></a>Uwagi  
 Wywoływanie `ScheduleTask` metoda niejawnie umieszcza liczba odwołań w grupie harmonogram, który zostanie usunięty w czasie wykonywania w odpowiednim czasie po wykonaniu zadania.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Currentscheduler — klasa](currentscheduler-class.md)   
 [Klasa harmonogramu](scheduler-class.md)   
 [Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



