on opening the file, I see a random encoding of alphabets and numbers.
On doing `file enc_flag` i see it is in ASCII code.
on opening the file i get the text:
`YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6YzRNalV3YUcxcWZRPT0nCg==`
i decode it from base64, and i get the output:
`b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzc4MjUwaG1qfQ=='`
it STILL Looks like a bas64 encoded string, so I decode it one more time(remove b' at the start):
`wpjvJAM{jhlzhy_k3jy9wa3k_78250hmj}`
almost looks like a flag, but i don't know what encoding is used this time, since it's very close to a flag i use caesar cipher. You get your flag then!
