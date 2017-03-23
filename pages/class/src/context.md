---
layout: class
title: Context
namespace: Freesewing
tags: [class documentation]
permalink: /class/context
---
## Description 

The [`Context`](context) class holds all information throughout an 
entire request lifecycle. It is perhaps the most important class in this project.

## Typical use

Every freesewing request is handled by this code in `index.php`:

```php?start_inline=1
$context = new \Freesewing\Context();
$context->setRequest(new \Freesewing\Request($_REQUEST));
$context->configure();

$context->runService();
```

## Public methods

### getApiDir

```php?start_inline=1
string getApiDir()
```

Returns the directory in which freesewing was installed.

#### Typical use
{:.no_toc}

Used by the [`InfoService`](services/infoservice) to discover available patterns, themes, and channels.

FIXME: Moved to Utils

### getChannel

```php?start_inline=1
\Freesewing\Channel getChannel() 
```
Returns the [`Channel`](/class/channels/core/channel) stored in the `channel` property, if any.

### getConfig

```php?start_inline=1
array getConfig() 
```
Returns the configuration array stored in the `config` property.

### getConfigFile

```php?start_inline=1
string getConfigFile() 
```
Returns the full filepath of the freesewing configuration file.

### getLocale

```php?start_inline=1
string getLocale() 
```
Returns the locale, which is a 2-letter string like `en` or `nl`.

### getMeasurementsSampler

```php?start_inline=1
\Freesewing\MeasurementsSampler getMeasurementsSampler() 
```
Returns the [`MeasurementsSampler`](measurementssampler) object in the `measurementsSampler` property, if any.

### getModel

```php?start_inline=1
\Freesewing\Model getModel() 
```
Returns the [`Model`](model) object in the `model` property, if any.

### getOptionsSampler

```php?start_inline=1
\Freesewing\OptionsSampler getOptionsSampler() 
```
Returns the [`OptionsSampler`](optionssampler) object in the `optionsSampler` property, if any.

### getPattern

```php?start_inline=1
\Freesewing\Pattern getPattern() 
```
Returns the [`Pattern`](patterns/core/pattern) object in the `pattern` property, if any.

> Given that [`Pattern`](patterns/core/pattern) is an abstract class, the actual object
> will be a (grand)child of the [`Pattern`](patterns/core/pattern) class.

### getRenderbot

```php?start_inline=1
\Freesewing\SvgRenderbot getRenderbot() 
```
Returns the [`SvgRenderbot`](svgrenderbot) object in the `renderbot` property, if any.

### getRequest

```php?start_inline=1
\Freesewing\Request getRequest() 
```
Returns the [`Request`](request) object in the `request` property, if any.

### getResponse

```php?start_inline=1
\Freesewing\Response getResponse() 
```
Returns the [`Response`](response) object in the `response` property, if any.

### getService

```php?start_inline=1
\Freesewing\Services\Service getService() 
```
Returns the [`Services\Service`](services/service) object in the `service` property, if any.

> Given that [`Services\Service`](services/service) is an 
> abstract class, the actual object  will be a child of the 
> [`Services\Service`](services/service) class.

### getSvgDocument

```php?start_inline=1
\Freesewing\SvgDocument getSvgDocument() 
```
Returns the [`SvgDocument`](svgdocument) object in the `svgDocument` property, if any.

### getTheme

```php?start_inline=1
\Freesewing\Themes\Theme getTheme() 
```
Returns the [`Themes\Theme`](themes/core/theme) object in the `theme` property, if any.

> Given that [`Themes\Theme`](themes/core/theme) is an abstract class
> the actual object  will be a child of the 
> [`Themes\Theme`](themes/core/theme) class.

### getTranslator

```php?start_inline=1
Symfony\Component\Translation\Translator getTranslator() 
```
Returns the `Translator` object in the `translator` property, if any.

> Translation is handled by [Symfony](http://symfony.com/)
> and documented [on their website](http://symfony.com/doc/current/translation.html).

### getUnits

```php?start_inline=1
array getUnits() 
```
Returns the array of units stored in the `units` property, if any.

The units array is structured as such:

```php?start_inline=1
[
    'in' => 'metric',
    'out' => 'imperial',
]
```

Units can be either `metric` or `imperial` and are divided into 
`in` units for user input (measurements and options) and `out`
metrics for output (things printed on the pattern).

{% include units.html %}

### setChannel

```php?start_inline=1
void setChannel(\Freesewing\Channels\Channel) 
```

Expects a [`Channels\Channel`](/class/channels/core/channel) object and stores it 
in the `channel` property.

> Given that [`Channels\Channel`](/class/channels/core/channel) is an
> abstract class, the actual object will be a child of the 
> [`Channels\Channel`](/class/channels/core/channel) class.

#### Typical use
{:.no_toc}

Called only from the [`Context::configure`](context#configure) method.

#### Parameters
{:.no_toc}

Expects a child of [`Channels\Channel`](/class/channels/core/channel).

### setConfig

```php?start_inline=1
void setConfig(array) 
```

Expects an array and stores it in the `config` property.

#### Typical use
{:.no_toc}

Called only from the [`Context::configure`](context#configure) method.

#### Parameters
{:.no_toc}

Expects an array.

### setLocale

```php?start_inline=1
void setLocale(string) 
```

Expects a string and stores it in the `locale` property.

#### Typical use
{:.no_toc}

Called only from the [`Context::configure`](context#configure) method.

#### Parameters
{:.no_toc}

Expects a string like `en` or `nl`.

### setMeasurementsSampler

```php?start_inline=1
void setMeasurementsSampler(\Freesewing\MeasurementsSampler) 
```

Expects a [`MeasurementsSampler`](measurementssampler) object and stores it 
in the `measurementsSampler` property.

#### Typical use
{:.no_toc}

Called only from the [`Context::addMeasurementsSampler`](context#addmeasurementssampler) method.

#### Parameters
{:.no_toc}

Expects an instance of [`MeasurementsSampler`](measurementssampler).

### setModel

```php?start_inline=1
void setModel(\Freesewing\Model) 
```

Expects a [`Model`](model) object and stores it 
in the `model` property.

#### Typical use
{:.no_toc}

Called only from the [`Context::addModel`](context#addmodel) method.

#### Parameters
{:.no_toc}

We all want a [`Model`](model), and so does this method.

### setOptionsSampler

```php?start_inline=1
void setOptionsSampler(\Freesewing\OptionsSampler) 
```

Expects a [`OptionsSampler`](optionssampler) object and stores it 
in the `optionsSampler` property.

#### Typical use
{:.no_toc}

Called only from the [`Context::addOptionsSampler`](context#addoptionssampler) method.

#### Parameters
{:.no_toc}

Expects an instance of [`OptionsSampler`](optionssampler).

### setPattern

```php?start_inline=1
void setPattern(\Freesewing\Patterns\Core\Pattern) 
```

Expects a (grand)child of [`Patterns\Core\Pattern`](patterns/core/pattern) and stores it 
in the `pattern` property.


#### Typical use
{:.no_toc}

Used by the [`Services\SampleService`](services/sampleservice) and 
[`Services\CompareService`](services/compareservice) to attach a pattern 
to the [`Context`](context). 

#### Parameters
{:.no_toc}

Expects a (grand)child of [`Patterns\Core\Pattern`](patterns/core/pattern).

### setRenderbot

```php?start_inline=1
void setRenderbot(\Freesewing\SvgRenderbot) 
```

Expects a [`SvgRenderbot`](svgrenderbot) object and stores it 
in the `renderbot` property.


#### Typical use
{:.no_toc}

Called only from the [`Context::addRenderbot`](context#addrenderbot) method.

#### Parameters
{:.no_toc}

Expects a [`SvgRenderbot`](svgrenderbot) object.

### setRequest

```php?start_inline=1
void setRequest(\Freesewing\Request) 
```

Expects a [`Request`](request) object and stores it 
in the `request` property.


#### Typical use
{:.no_toc}

Called from `index.php` to store the user request.

#### Parameters
{:.no_toc}

Expects a [`Request`](request) object.

### setResponse

```php?start_inline=1
void setResponse(\Freesewing\Response) 
```

Expects a [`Response`](response) object and stores it 
in the `response` property.


#### Typical use
{:.no_toc}

Used by the `run` method of all services 
to attach a [`Response`](response) object to the [`Context`](context).

Specifically:

- [`InfoService::run`](/class/services/infoservice#run) 
- [`DraftService::run`](/class/services/draftservice#run) 
- [`SampleService::run`](/class/services/sampleservice#run) 
- [`CompareService::run`](/class/services/compareservice#run) 

#### Parameters
{:.no_toc}

Expects a [`Request`](request) object.

### setService

```php?start_inline=1
void setService(\Freesewing\Services\Service) 
```

Expects a child of [`Services\Service`](services/service) 
and stores it in the `service` property.

#### Typical use
{:.no_toc}

Called by [`Context::configure`](context#configure).

#### Parameters
{:.no_toc}

Expects a child of [`Services\Service`](services/service).

### setSvgDocument

```php?start_inline=1
void setSvgDocument(\Freesewing\SvgDocument) 
```

Expects an [`SvgDocument`](svgdocument) object
and stores it in the `svgDocument` property.

#### Typical use
{:.no_toc}

Not used. We call [`Context::addSvgDocument`](context#addsvgdocument) instead.

#### Parameters
{:.no_toc}

Expects an instance of [`SvgDocument`](svgdocument).

### setTheme

```php?start_inline=1
void setTheme(\Freesewing\Themes\Theme) 
```

Expects a child of [`Themes\Theme`](themes/core/theme) 
and stores it in the `theme` property.

#### Typical use
{:.no_toc}

Called by [`Context::configure`](context#configure).

#### Parameters
{:.no_toc}

Expects a child of [`Themes\Theme`](themes/core/theme).

### configure

```php?start_inline=1
void configure()
```

The configure method sets up properties that are common to all requests.

They are:
- config: Holds the configuration file as an array
- service: Holds a [`Service`](services/service) object 
- channel: Holds a [`Channel`](/class/channels/core/channel) object 
- theme: Holds a [`Themes\Theme`](themes/core/theme) object 
- locale: Holds a string with the locale

#### Typical use
{:.no_toc}

Called from `index.php`, the code that handles all freesewing requests.

### addPattern

```php?start_inline=1
void addPattern()
```

Loads pattern in the pattern property.

Also lets the pattern know whether we are dealing with a paperless theme by feeding
[`Theme::isPaperless`](/class/themes/core/theme#ispaperless) into [`Pattern::setPaperless`](/class/patterns/core/pattern#setpaperless)

#### Typical use
{:.no_toc}

Used by the `run` method of all services 
to attach a [`Pattern`](patterns/core/pattern) object to the [`Context`](context).

Specifically:

- [`InfoService::run`](/class/services/infoservice#run) 
- [`DraftService::run`](/class/services/draftservice#run) 
- [`SampleService::run`](/class/services/sampleservice#run) 
- [`CompareService::run`](/class/services/compareservice#run) 

> Given that [`Pattern`](patterns/core/pattern) is an abstract class, the actual object is always
> a (grand)child of the [`Pattern`](patterns/core/pattern) class.

### addModel

```php?start_inline=1
void addModel()
```

Instantiates a new [`Model`](model) object and calls
[`Context::setModel`](context#setmodel) with it.

#### Typical use
{:.no_toc}

Used by [`SampleService::run`](/class/services/sampleservice#run) and [`DraftService::run`](/class/services/draftservice#run)
to attach a [`Model`](model) object to the [`Context`](context).

### addUnits

```php?start_inline=1
void addUnits()
```

Stores the units array in the `units` property.

#### Typical use
{:.no_toc}

Used by the `run` method of all rendering services 
to store an array of units in the [`Context`](context) units property.

Specifically:

- [`DraftService::run`](/class/services/draftservice#run) 
- [`SampleService::run`](/class/services/sampleservice#run) 
- [`CompareService::run`](/class/services/compareservice#run) 

{% include units.html %}

### addTranslator

```php?start_inline=1
void addTranslator()
```

Stores a symfony Translator object in the `translator` property.

#### Typical use
{:.no_toc}

Used by the `run` method of all rendering services 
to attach a symfony Translator object to the [`Context`](context).

Specifically:

- [`DraftService::run`](/class/services/draftservice#run) 
- [`SampleService::run`](/class/services/sampleservice#run) 
- [`CompareService::run`](/class/services/compareservice#run) 

### addRenderBot

```php?start_inline=1
void addRenderBot()
```

Instantiates a new [`SvgRenderbot`](svgrenderbot) object and calls
[`Context::setRenderbot`](context#setrenderbot) with it.

#### Typical use
{:.no_toc}

Used by the `run` method of all rendering services 
to attach a [`SvgRenderbot`](svgrenderbot) object to the [`Context`](context).

Specifically:

- [`DraftService::run`](/class/services/draftservice#run) 
- [`SampleService::run`](/class/services/sampleservice#run) 
- [`CompareService::run`](/class/services/compareservice#run) 

> Freesewing allows to use a different renderbot, in case you want to output a 
> different format. 
> However, there is currently only one renderbot, the [`SvgRenderbot`](svgrenderbot).
> As such, this method will always instantiate an [`SvgRenderbot`](svgrenderbot)

### addSvgDocument

```php?start_inline=1
void addSvgDocument()
```

Loads an [`SvgDocument`](svgdocument) in the `svgDocument` property.

#### Typical use
{:.no_toc}

Used by the `run` method of all rendering services 
to attach a [`SvgDocument`](svgdocument) object to the [`Context`](context).

Specifically:

- [`DraftService::run`](/class/services/draftservice#run) 
- [`SampleService::run`](/class/services/sampleservice#run) 
- [`CompareService::run`](/class/services/compareservice#run) 

### addOptionsSampler

```php?start_inline=1
void addOptionsSampler()
```

Instantiates a new [`OptionsSampler`](optionssampler) object and calls
[`Context::setOptionsSampler`](context#setoptionssampler) with it.

#### Typical use
{:.no_toc}

Used by [`SampleService::run`](/class/services/sampleservice#run) 
to attach a [`OptionsSampler`](optionssampler) object to the [`Context`](context).

### addMeasurementsSampler

```php?start_inline=1
void addMeasurementsSampler()
```

Instantiates a new [`MeasurementsSampler`](measurementssampler) object and calls
[`Context::setMeasurementssampler`](context#setmeasurementssampler) with it.

#### Typical use
{:.no_toc}

Used by [`SampleService::run`](/class/services/sampleservice#run) and [`CompareService::run`](/class/services/compareservice#run)
to attach a [`MeasurementsSampler`](measurementssampler) object to the [`Context`](context).

### runService

```php?start_inline=1
void runService() 
```

Calls the `run` method on the [`Services\Service`](services/service) 
object in the `service` property.

> Given that [`Services\Service`](services/service) is an
> abstract class, the actual object will be a child of the 
> [`Services\Service`](services/service) class.

#### Typical use
{:.no_toc}

Called only from `index.php`, the code that handles all freesewing requests.

### cleanUp

```php?start_inline=1
void cleanUp()
```

Calls [`Theme::cleanUp`](/class/themes/core/theme#cleanup) and [`Channel::cleanUp`](/class/channels/core/channel#cleanup).

If a pattern is attached to the [`Context`](context), this also calls
[`Pattern::cleanUp`](/class/patterns/core/pattern#cleanup).

> <b>How do you mean, 'If a pattern is attached'?</b>
> 
> This check is needed because the infoservice does not always instantiate a [`Pattern`](patterns/core/pattern).

This is a way to allow patterns, themes, and channels to clean up at the end of
a request. For example, if you're logging to a database in your channel,
this will make sure you get a chance to close that connection in your channel's
`cleanUp` method.

#### Typical use
{:.no_toc}

Used by the `run` method of all rendering services 
to attach a symfony Translator object to the [`Context`](context).

Specifically:

- [`DraftService::run`](/class/services/draftservice#run) 
- [`SampleService::run`](/class/services/sampleservice#run) 
- [`CompareService::run`](/class/services/compareservice#run) 

## See also
{% include classFooter.html %}
* TOC - Do not remove this line
{:toc}

