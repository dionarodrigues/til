# Plop - Micro generator framework

__[Plop](https://plopjs.com/) is a little tool that saves you time and helps your team build new files with consistency. Plop generates code when you want, how you want, and can be changed whenever you want.__

Ive been using this amazing tool to generate new component files for my React applications, but we can use it for many types of code structure using Node.js.

I'll show how we can set this tool for React projects, but feel free to adapt it to your  project needs. 

## Add plop to your project

```
yarn add plop --dev
```

## Create a plopfile.js

You can create a plopfile.js at the root of your project, but I like to have a specify directory to manage all plop files.

__generators/plopfile.js__

```
module.exports = (plop) => {
  plop.setGenerator('component', {
    description: 'Create a component',
    prompts: [
      {
        type: 'input',
        name: 'name',
        message: 'What is your component name?'
      }
    ],
    actions: [
      {
        type: 'add',
        path: '../src/components/{{pascalCase name}}/index.tsx',
        templateFile: 'templates/Component.tsx.hbs'
      },
      {
        type: 'add',
        path: '../src/components/{{pascalCase name}}/styles.ts',
        templateFile: 'templates/styles.ts.hbs'
      },
      {
        type: 'add',
        path: '../src/components/{{pascalCase name}}/stories.tsx',
        templateFile: 'templates/stories.tsx.hbs'
      },
      {
        type: 'add',
        path: '../src/components/{{pascalCase name}}/test.tsx',
        templateFile: 'templates/test.tsx.hbs'
      }
    ]
  })
}
```

__generators/templates/Component.tsx.hbs__

```
import * as S from './styles'

const {{pascalCase name}} = ({ title='{{pascalCase name}} Title' }) => (
  <S.Wrapper>
    <h1>{title}</h1>
  </S.Wrapper>
)

export default {{pascalCase name}}
```

__generators/templates/stories.tsx.hbs__

```
import { withKnobs, text } from '@storybook/addon-knobs'
import {{pascalCase name}} from './'

export default {
  title: '{{pascalCase name}}',
  component: {{pascalCase name}},
  decorators: [withKnobs]
}

export const Default = () => (
  <{{pascalCase name}}
    title={text('Title', '{{pascalCase name}} Title')}
  />
)
```

__generators/templates/styles.ts.hbs__

```
import styled from 'styled-components'

export const Wrapper = styled.div``
```

__generators/templates/test.tsx.hbs__

```
import { render, screen } from '@testing-library/react'

import {{pascalCase name}} from '.'

describe('<{{pascalCase name}} />', () => {
  it('should render the heading', () => {
    const { container } = render(<{{pascalCase name}} />)

    expect(screen.getByRole('heading', { name: /{{pascalCase name}}/i })).toBeInTheDocument()

    expect(container.firstChild).toMatchSnapshot()
  })
})
```

As you can see, in the plopfile.js file we can define all files and actions we want to generate.

I'm also using [handlebars](https://handlebarsjs.com/) in my files.

## Add the command in the package.json

```
"generate": "yarn plop --plopfile generators/plopfile.js",
```

-- 

Learn more about it in the [Plop documentation](https://plopjs.com/documentation/).

Take a look at my [nextjs-typescript-starter](https://github.com/diogorodrigues/nextjs-typescript-starter) to have a better understanding of this use. 👌😎
