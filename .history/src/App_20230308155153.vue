new Vue({
  el: '#app',
  data: { 
    attrs: [
        {
          key: 'today',
          highlight: {
            animated: true,
            height: '1.8rem',
            backgroundColor: 'red',
            borderColor: null,
            borderWidth: '1px',
            borderStyle:'solid',
            borderRadius:'1.8rem',
            opacity: 1
          },
          dates: new Date(),
          popover: {
            label: 'メッセージを表示できます',
          },
        }
    ],
  }
})