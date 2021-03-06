<template>
  <div class="page">
    <au-panel class="section" title="组件描述">
      <p class="paragraph">
        一个简单的JSON Schema编辑器，用于生成和编辑JSON-Schema，支持<span class="code au-theme-radius au-theme-background-color--warning-bottom">v-model</span>。
      </p>
      <!-- 组件示例 -->
      <div class="component-example">
        <au-json-schema
          v-model="jsonSchema"
          :custom-schema-properties="customSchemaProperties"
          label="JSON Schema 编辑器"/>
      </div>
      <!-- 组件示例 -->
    </au-panel>
    <au-panel class="section" title="Props">
      <au-table>
        <thead>
          <tr>
            <th>字段</th>
            <th>必填</th>
            <th>类型</th>
            <th>默认</th>
            <th>可选</th>
            <th>说明</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>label</td>
            <td>
              <!-- <au-icon type="check" class="au-theme-color--success"></au-icon> -->
              <au-icon type="times"></au-icon>
            </td>
            <td>String</td>
            <td><au-icon type="minus"></au-icon></td>
            <td><au-icon type="minus"></au-icon></td>
            <td>
              标题文字
            </td>
          </tr>
          <tr>
            <td>schema</td>
            <td>
              <au-icon type="check" class="au-theme-color--success"></au-icon>
              <!-- <au-icon type="times"></au-icon> -->
            </td>
            <td>Object</td>
            <td><au-icon type="minus"></au-icon></td>
            <td>
              <a class="au-theme-color--info" href="https://json-schema.org/" target="_blank">JSON Schema</a>
              格式的对象<br>
            </td>
            <td>
              JSON Schema 对象<br>
            </td>
          </tr>
          <tr>
            <td>custom-schema-propertie</td>
            <td>
              <!-- <au-icon type="check" class="au-theme-color--success"></au-icon> -->
              <au-icon type="times"></au-icon>
            </td>
            <td>
              Array<br>
              - Object
            </td>
            <td>
              <au-icon type="times"></au-icon>
            </td>
            <td>
              <ol class="option-list">
                -key:属性的key<br>
                -text:属性的描述<br>
                -type:属性的类型<br>
                --boolean<br>
                --number<br>
                --integer<br>
                --string<br>
                -default:该属性的默认值
              </ol>
            </td>
            <td>
              自定义schema属性<br>
              其中key和text为必填项，type为选填项，不指定则与当前项本身的类型保持一致<br>
              key不能是schema的官方保留字：'type'/'items'/'properties'<br>
              default可以是字面量也可以是函数，当是函数的时候接受一个参数type表示当前描述项的类型，通常在不指定type时使用函数
            </td>
          </tr>
          <tr>
            <td>types</td>
            <td>
              <!-- <au-icon type="check" class="au-theme-color--success"></au-icon> -->
              <au-icon type="times"></au-icon>
            </td>
            <td>
              Array <br>
              - String
            </td>
            <td>
              所有可选类型
            </td>
            <td>
              <ol class="option-list">
                <li class="au-theme-border-color--base-8">boolean</li>
                <li class="au-theme-border-color--base-8">integer</li>
                <li class="au-theme-border-color--base-8">number</li>
                <li class="au-theme-border-color--base-8">string</li>
                <li class="au-theme-border-color--base-8">object</li>
                <li class="au-theme-border-color--base-8">array</li>
              </ol>
            </td>
            <td>
              可用的数据类型<br>
            </td>
          </tr>
          <tr>
            <td>root-types</td>
            <td>
              <!-- <au-icon type="check" class="au-theme-color--success"></au-icon> -->
              <au-icon type="times"></au-icon>
            </td>
            <td>
              Array <br>
              - String
            </td>
            <td>
              所有可选类型
            </td>
            <td>
              <ol class="option-list">
                <li class="au-theme-border-color--base-8">boolean</li>
                <li class="au-theme-border-color--base-8">integer</li>
                <li class="au-theme-border-color--base-8">number</li>
                <li class="au-theme-border-color--base-8">string</li>
                <li class="au-theme-border-color--base-8">object</li>
                <li class="au-theme-border-color--base-8">array</li>
              </ol>
            </td>
            <td>
              根节点可用的数据类型<br>
            </td>
          </tr>
          <tr>
            <td>form-item-size</td>
            <td>
              <!-- <au-icon type="check" class="au-theme-color--success"></au-icon> -->
              <au-icon type="times"></au-icon>
            </td>
            <td>
              String
            </td>
            <td>
              normal
            </td>
            <td>
              <ol class="option-list">
                <li class="au-theme-border-color--base-8">large</li>
                <li class="au-theme-border-color--base-8">normal</li>
                <li class="au-theme-border-color--base-8">small</li>
                <li class="au-theme-border-color--base-8">mini</li>
              </ol>
            </td>
            <td>
              表单项的尺寸<br>
            </td>
          </tr>
          <tr>
            <td>root-name</td>
            <td>
              <!-- <au-icon type="check" class="au-theme-color--success"></au-icon> -->
              <au-icon type="times"></au-icon>
            </td>
            <td>
              String
            </td>
            <td>
              <au-icon type="minus"></au-icon>
            </td>
            <td>
              <au-icon type="minus"></au-icon>
            </td>
            <td>
              根节点的名称，仅用于显示<br>
            </td>
          </tr>
        </tbody>
      </au-table>
    </au-panel>
    <au-panel class="section" title="Slots">
      <!-- <au-table>
        <thead>
          <tr>
            <th>名称</th>
            <th>说明</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>slot1</td>
            <td>
              该slot的详细说明
            </td>
          </tr>
        </tbody>
      </au-table> -->
      <au-icon type="minus"></au-icon>
    </au-panel>
    <au-panel class="section" title="Events">
      <au-table>
        <thead>
          <tr>
            <th>名称</th>
            <th>参数</th>
            <th>说明</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>change</td>
            <td>
              schema
            </td>
            <td>
              Schema被用户修改时触发<br>
              参数schema为最新的schema <br>
            </td>
          </tr>
        </tbody>
      </au-table>
    </au-panel>
    <au-panel class="section" title="Methods">
      <!-- <au-table>
        <thead>
          <tr>
            <th>名称</th>
            <th>参数</th>
            <th>说明</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>method1</td>
            <td>
              <ol class="option-list">
                <li class="au-theme-border-color--base-8">arg1</li>
                <li class="au-theme-border-color--base-8">arg2</li>
              </ol>
            </td>
            <td>
              该方法及参数的详细说明
            </td>
          </tr>
        </tbody>
      </au-table> -->
      <au-icon type="minus"></au-icon>
    </au-panel>
    <au-panel class="section" title="使用示例">
      <h4 class="title-1">基础用例</h4>
      <code-h lang="html" content='
        <au-json-schema
          v-model="jsonSchema"
          :custom-schema-properties="customSchemaProperties"
          label="JSON Schema 编辑器"/>
      '></code-h>
      <code-h lang="js">
        export default {
        data () {
          return {
            jsonSchema: {
              type: 'object',
              properties: {
                'a': {
                  type: 'string'
                },
                'b': {
                  type: 'array',
                  items: {
                    type: 'string'
                  }
                }
              }
            },
            customSchemaProperties: [
              {
                key: 'init',
                text: '初始值',
                default (type) {
                  switch (type) {
                    case 'string': return 'test'
                    case 'boolean': return false
                    case 'number':
                    case 'integer': return 999
                  }
                }
              },
              {
                key: 'vala',
                text: 'VALA',
                type: 'boolean',
                default: false
              }
            ]
          }
        },
        watch: {
          jsonSchema (v) {
            console.log(JSON.stringify(v))
          }
        }
      }
      </code-h>
    </au-panel>
  </div>
</template>

<script>
export default {
  name: 'json-schema',
  data () {
    return {
      jsonSchema: {
        type: 'object',
        properties: {
          'a': {
            type: 'string'
          },
          'b': {
            type: 'array',
            items: {
              type: 'string'
            }
          }
        }
      },
      customSchemaProperties: [
        {
          key: 'init',
          text: '初始值',
          default (type) {
            switch (type) {
              case 'string': return 'test'
              case 'boolean': return false
              case 'number':
              case 'integer': return 999
            }
          }
        },
        {
          key: 'vala',
          text: 'VALA',
          type: 'boolean',
          default: false
        }
      ]
    }
  },
  watch: {
    jsonSchema (v) {
      console.log(JSON.stringify(v))
    }
  }
}
</script>
