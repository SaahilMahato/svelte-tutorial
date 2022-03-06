<script>
    import {createEventDispatcher} from 'svelte';

    let selected = 5;

    const dispatch = createEventDispatcher();

    const onChange = (e) => {
        selected = e.currentTarget.value;
        dispatch('rating-select', selected);
    }
</script>

<ul class="rating">
    <li>
        <input
            type="radio"
            id="num1"
            name="rating"
            value="1"
            on:change={onChange}
            checked={selected===1}
        />
        <label for="num1">1</label>
    </li>
    <li>
        <input
            type="radio"
            id="num2"
            name="rating"
            value="2"
            on:change={onChange}
            checked={selected===2}
        />
        <label for="num2">2</label>
    </li>
    <li>
        <input
            type="radio"
            id="num3"
            name="rating"
            value="3"
            on:change={onChange}
            checked={selected===3}
        />
        <label for="num3">3</label>
    </li>
    <li>
        <input
            type="radio"
            id="num4"
            name="rating"
            value="4"
            on:change={onChange}
            checked={selected===4}
        />
        <label for="num4">4</label>
    </li>
    <li>
        <input
            type="radio"
            id="num5"
            name="rating"
            value="5"
            on:change={onChange}
            checked={selected===5}
        />
        <label for="num5">5</label>
    </li>
</ul>

<style>
    .rating {
      display: flex;
      align-items: center;
      justify-content: space-around;
      margin: 30px 0;
    }
    .rating li {
      position: relative;
      background: #f4f4f4;
      width: 30px;
      height: 30px;
      padding: 10px;
      text-align: center;
      border-radius: 50%;
      font-size: 19px;
      border: 1px #eee solid;
      transition: 0.3s;
    }
    .rating li label {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 30px;
      height: 30px;
      padding: 10px;
      border-radius: 50%;
      transform: translate(-50%, -50%);
      cursor: pointer;
    }
    .rating li:hover {
      background: #ff6a95;
      color: #fff;
    }
    /* Make actual radio select invisible */
    [type='radio'] {
      opacity: 0;
    }
    /* Use the sibling select */
    [type='radio']:checked ~ label {
      background: #ff6a95;
      color: #fff;
    }
  </style>