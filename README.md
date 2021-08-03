# mcp - My Colony Python

  [![DeepSource](https://deepsource.io/gh/MCW-My-Colony-Wiki/MyColonyFileParser.svg/?label=active+issues&show_trend=true&token=zjOyAP4RLEuWcm5YOU1NQJW_)](https://deepsource.io/gh/MCW-My-Colony-Wiki/MyColonyFileParser/?ref=repository-badge)
  
  [中文版readme](README_zh.md)
  
  current not suppot My Colony 2

## Index of content

- [Config](##Config)
- [Classes](##Classes)
  - [Base](###Base)
    - [CommonBase](####CommonBase)
    - [DictBase](####DictBase)
    - [ListBase](####ListBase)
  - [FileBase](###FileBase)
  - [CategoryBase](###CategoryBase)
    - [DictCategory](####DictCategory)
    - [ListCategory](####ListCategory)
  - [UnitBase](###UnitBase)
    - [DictUnit](####DictUnit)
    - [ListUnit](####ListUnit)

## Config

- Description: this module use `configparser` that in stdlib to provide config function
- Path: `mcfp.config.config`
- Sections
  - `network`
    - Options
      - `timeout`(int, default=3): timeout of all the network related function

## Classes

### Base

#### CommonBase

- Description: provide generic method
- Path: `mcfp.base.CommonBase`
- Method
  - `__delattr__`: disable `del object.attr`
  - `__str__`: return `self.name`

#### DictBase

- Description: provide method of `dict` object
- Path: `mcfp.base.DictBase`
- Inherit: [CommonBase](####CommonBase)

#### ListBase

- Description: provide method of `list` object
- Path: `mcfp.base.ListBase`
- Inherit: [CommonBase](####CommonBase)

### FileBase

- Description: basically same as `dict` object
- Path: `mcfp.filebase.FileBase`
- Inherit: [DictBase](####DictBase)
- Attributes
  - `name`: file name
  - `dict`: file data
- Method
  - `categories`: alias of `file.keys()`

### CategoryBase

- Path: `mcfp.categorybase.CategoryBase`
- Common attributes
  - `file`: instance of subclass of FileBase which this category belong
  - `name`: category name
  - `data`: category data
- Common method
  - `units`: Implemented by subclass

#### DictCategory

- Description: basically same as `dict` object
- Path: `mcfp.category.DictCategory`
- Inherit: [DictBase](####DictBase), [CategoryBase](###CategoryBase)
- Attributes
  - `dict`: alias of `self.data`
- Method
  - `units`: alias of `self.keys`

#### ListCategory

- Description: basically same as `list` object
- Path: `mcfp.category.ListCategory`
- Inherit: [ListBase](####ListBase), [CategoryBase](###CategoryBase)
- Attributes
  - `list`: alias of `self.data`
- Method
  - `units`: similar with `self.__iter__` but return str object

### UnitBase

- Path: `mcfp.unitbase.UnitBase`
- Common attributes
  - `file`: instance of subclass of FileBase which this unit belong, same as `category.file`
  - `category`: instance of subclass of CategoryBase which this unit belong
  - `data`: unit data

#### DictUnit

- Description: basically same as `dict` object
- Path: `mcfp.unit.DictUnit`
- Inherit: [DictBase](####DictBase), [UnitBase](###UnitBase)

#### ListUnit

- Description: basically same as `list` object
- Path: `mcfp.unit.ListUnit`
- Inherit: [ListBase](####ListBase), [UnitBase](###UnitBase)
