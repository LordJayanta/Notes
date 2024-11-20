# create model 

### STEP 1: Create root element

*index.html*
```jsx
<body>
    <div id="root"></div>
    <div id="root-model"></div>
    <script type="module" src="/src/main.jsx"></script>
</body>
```


### STEP 2: Create model component
*model.jsx*
```jsx
import React from "react";
import ReactDOM from "react-dom"

const Model = ({ children, onOpen, onClose }) => {
    if (!onOpen) return null;
    return ReactDOM.createPortal(
        (
            <div></div>
        ),
        document.querySelector('#root-model')
    )
}

export default Model
```


```jsx
import React from "react";
import ReactDOM from "react-dom"

const Model = ({ children, onOpen, onClose, setHeight, setWidth, className, ...props }) => {
    if (!onOpen) return null;
    return ReactDOM.createPortal(
        (
            <div className='fixed top-0 left-0 h-screen w-full' style={{ backgroundColor: 'rgb(0,0,0,0.5' }}>
                <div className="wrapper relative h-full w-full m-auto flex justify-center items-center">
                    <button className='absolute top-10 right-[10%] text-white hover:text-blue-500' style={{ right: '10%', top: '5%' }} onClick={onClose}>
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width={40} height={40} color={"#"} fill={"none"}>
                            <path d="M19.0005 4.99988L5.00045 18.9999M5.00045 4.99988L19.0005 18.9999" stroke="currentColor" strokeWidth="1.5" strokeLinecap="round" strokeLinejoin="round" />
                        </svg>
                    </button>
                    <div className={`${className} bg-slate-800 text-white rounded-xl shadow-2xl overflow-auto p-10 m-3`} style={{ height: setHeight, width: setWidth }}>
                        {children}
                    </div>
                </div>
            </div>
        ),
        document.querySelector('#root-model')
    )
}

export default Model
```


### STEP 3: use Model

```jsx
import Model from '../Model'
```
```jsx
const [isShowBatchData, setIsShowBatchData] = useState(false)
```
1st:
```jsx
<Model
    open={isShowBatchData}
    onClose={() => { setIsShowBatchData(false) }}
    setHeight={'fit-content'}
    setWidth={'fit-content'}
>
    <CalculateData data={showBatchData} />
</Model>
```
2nd:
```jsx
<Model
    open={isShowBatchData}
    onClose={() => { setIsShowBatchData(false) }}
    setHeight={'fit-content'}
    setWidth={'fit-content'}
    children={<CalculateData data={showBatchData} />}
/>
    
```
### STEP 2: Create model component

```jsx

```
